# Transforming Data

## noncontextual transformations

* noncontextual transformations coincide with t in the EtLT subpattern
* refers to transformations independent of business logic or data modeling
* e.g. deduplicating records (might occur due to mistake, or backfilling overlapping with subsequent data load)
* can be identified via SQL via grouping (SELECT ... GROUP BY ... HAVING COUNT(*) > 1) or window functions (SELECT ..., ROW_NUMBER() OVER(PARTITION BY ...) FROM ...)
* e.g. parsing individual parameters from an URL (like `https://www.mydomain.com/page-name?utm_content=textlink&utm_medium=social&utm_source=twitter&utm_campaign=fallsale`)
* can be handled with urllib3 lib
* snowflake has a PARSE_URL command

## when to transform? during or after ingestion?

* technically, noncontextual transformations can happen during or after ingestion
* reasons to do suring ingestion (EtLT):
  * transformation is easiest outside SQL
  * transformation is addressing data quality, which should be done as early as possible

## data modeling foundations

* key terms:
  * measures, e.g. customer count, dollar revenue
  * attributes = filter or grouping criteria, e.g. dates, countries
  * granularity, e.g. daily orders vs hourly orders
  * source tables = tables populated by data ingestion
  
### modeling fully refreshed data

* suppose we are given an Orders and Customers table
* create a data model to answer how much revenue was generated from a given country in a given month, or how many orders were placed on a given day
* thus we need measures total revenue and order count, attributes order country and order date, with daily granularity (smallest unit required but no less)

```sql
CREATE TABLE IF NOT EXISTS order_summary_daily (
    order_date date,
    order_country varchar(10),
    total_revenue numeric,
    order_count int
);

INSERT INTO order_summary_daily
    (order_date, order_country,
    total_revenue, order_count)
SELECT
    o.OrderDate AS order_date,
    c.CustomerCountry AS order_country,
    SUM(o.OrderTotal) as total_revenue,
    COUNT(o.OrderId) AS order_count
FROM Orders o
INNER JOIN Customers c on
    c.CustomerId = o.CustomerId
GROUP BY o.OrderDate, c.CustomerCountry;

-- How much revenue was generated from orders placed from a given country in a given month?
SELECT
    DATE_PART('month', order_date) as order_month,
    order_country,
    SUM(total_revenue) as order_revenue
FROM order_summary_daily
GROUP BY
    DATE_PART('month', order_date),
    order_country
ORDER BY
    DATE_PART('month', order_date),
    order_country;

-- How many orders were placed on a given day?
SELECT
    order_date,
    SUM(order_count) as total_orders
FROM order_summary_daily
GROUP BY order_date
ORDER BY order_date;
```

### modeling with tracking historic changes, slowly changing dimensions (SDC) for fully refreshed data

* add new record to table for each change of entity including a valid date range (can use null or something like 2199-12-31 for active record)
* keeping SCD up to date can be challenging, more details in Kimball's DWH book

```sql
SELECT
    o.OrderId,
    o.OrderDate,
    c.CustomerName,
    c.CustomerCountry
FROM Orders o
INNER JOIN Customers_scd c
    ON o.CustomerId = c.CustomerId
        AND o.OrderDate BETWEEN c.ValidFrom AND
        c.Expired
ORDER BY o.OrderDate;
```

### modeling incrementally ingested data

* customers table has same id multiple times with different LastUpdated column
* match given order to customer in this point in time (pit) using CTE (common table expression)

```sql
CREATE TABLE order_summary_daily_pit
(
    order_date date,
    order_country varchar(10),
    total_revenue numeric,
    order_count int
);

INSERT INTO order_summary_daily_pit
    (order_date, order_country, total_revenue, order_count)
WITH customer_pit AS
(
    SELECT
        cs.CustomerId,
        o.OrderId,
        MAX(cs.LastUpdated) AS max_update_date
    FROM Orders o
    INNER JOIN Customers_staging cs
        ON cs.CustomerId = o.CustomerId
            AND cs.LastUpdated <= o.OrderDate
    GROUP BY cs.CustomerId, o.OrderId
)
SELECT
    o.OrderDate AS order_date,
    cs.CustomerCountry AS order_country,
    SUM(o.OrderTotal) AS total_revenue,
    COUNT(o.OrderId) AS order_count
FROM Orders o
INNER JOIN customer_pit cp
    ON cp.CustomerId = o.CustomerId
        AND cp.OrderId = o.OrderId
INNER JOIN Customers_staging cs
    ON cs.CustomerId = cp.CustomerId
        AND cs.LastUpdated = cp.max_update_date
GROUP BY o.OrderDate, cs.CustomerCountry;

SELECT
    DATE_PART('month', order_date) AS order_month,
    order_country,
    SUM(total_revenue) AS order_revenue
FROM order_summary_daily_pit
GROUP BY
    DATE_PART('month', order_date),
    order_country
ORDER BY
    DATE_PART('month', order_date),
    order_country;
```

### modeling append-only data

* immutable data, e.g. never changing eventls like page views of a website
* similar to fully refreshed case, but can take advantage of immutability
* suppose we are given a pageview table (customer id, view time, url, utm_medium)
* model for getting page views for each url by day?, page views from each country each day?
* => granularity -- daily; attributes -- date, url, customer country; metric -- page views
* initial model

```sql
CREATE TABLE pageviews_daily (
    view_date date,
    url_path varchar(250),
    customer_country varchar(50),
    view_count int
);

INSERT INTO pageviews_daily
    (view_date, url_path, customer_country, view_count)
SELECT
    CAST(p.ViewTime as Date) AS view_date,
    p.UrlPath AS url_path,
    c.CustomerCountry AS customer_country,
    COUNT(*) AS view_count
FROM PageViews p
LEFT JOIN Customers c ON c.CustomerId = p.CustomerId
GROUP BY
    CAST(p.ViewTime as Date),
    p.UrlPath,
    c.CustomerCountry;

SELECT
    view_date,
    customer_country,
    SUM(view_count)
FROM pageviews_daily
GROUP BY view_date, customer_country
ORDER BY view_date, customer_country;
```

* how to react to next ingestion that adds more records?
  * truncate pageviews_daily, rerun insert (full refresh), less complex, prefer if low runtime
  * only insert new records (incremental refresh), beware timestamp granularity

```sql
CREATE TABLE tmp_pageviews_daily AS
SELECT *
FROM pageviews_daily
WHERE view_date
    < (SELECT MAX(view_date) FROM pageviews_daily);

INSERT INTO tmp_pageviews_daily
    (view_date, url_path, customer_country, view_count)
SELECT
    CAST(p.ViewTime as Date) AS view_date,
    p.UrlPath AS url_path,
    c.CustomerCountry AS customer_country,
    COUNT(*) AS view_count
FROM PageViews p
LEFT JOIN Customers c
    ON c.CustomerId = p.CustomerId
WHERE p.ViewTime
    > (SELECT MAX(view_date) FROM pageviews_daily)
GROUP BY
    CAST(p.ViewTime as Date),
    p.UrlPath,
    c.CustomerCountry;

TRUNCATE TABLE pageviews_daily;

INSERT INTO pageviews_daily
SELECT * FROM tmp_pageviews_daily;

DROP TABLE tmp_pageviews_daily;
```

### modeling change capture data

* suppose we have a Orders_cdc table, where an additional column EventType (insert, update, delete) exists
* how to report on current status?

```sql
CREATE TABLE orders_current (
    order_status varchar(20),
    order_count int
);

INSERT INTO orders_current
    (order_status, order_count)
WITH o_latest AS
(
    SELECT
        OrderId,
        MAX(LastUpdated) AS max_updated
    FROM Orders_cdc
    GROUP BY orderid
)
SELECT o.OrderStatus,
    Count(*) as order_count
FROM Orders_cdc o
INNER JOIN o_latest
    ON o_latest.OrderId = o_latest.OrderId
        AND o_latest.max_updated = o.LastUpdated
WHERE o.EventType <> 'delete'
GROUP BY o.OrderStatus;
```

* how to make sense of changes themselves, e.g. how long does it take until shipping?

```sql
CREATE TABLE orders_time_to_ship (
    OrderId int,
    backordered_days interval
);

INSERT INTO orders_time_to_ship
    (OrderId, backordered_days)
WITH o_backordered AS
(
SELECT
        OrderId,
        MIN(LastUpdated) AS first_backordered
    FROM Orders_cdc
    WHERE OrderStatus = 'Backordered'
    GROUP BY OrderId
),
o_shipped AS
(
SELECT
        OrderId,
        MIN(LastUpdated) AS first_shipped
    FROM Orders_cdc
    WHERE OrderStatus = 'Shipped'
    GROUP BY OrderId
)
SELECT b.OrderId,
    first_shipped - first_backordered
        AS backordered_days
FROM o_backordered b
INNER JOIN o_shipped s on s.OrderId = b.OrderId;
```
