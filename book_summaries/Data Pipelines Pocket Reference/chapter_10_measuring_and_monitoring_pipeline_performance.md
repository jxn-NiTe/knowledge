# Measuring and Monitoring Pipeline Performance

## Key Pipeline Metrics

* choosing metrics should start with identifying what matters to you and your stakeholders, possible examples
  * how many validation tests are run and how many pass
  * how frequently a specific DAG runs successfully
  * total runtime of a pipeline over the course of weeks / months / years
* try to focus on fewer but important metrics

## Prepping the Data Warehouse

* store metrics in dedicated tables, e.g.

```sql
CREATE TABLE dag_run_history (
    id int,
    dag_id varchar(250),
    execution_date timestamp with time zone,
    state varchar(250),
    run_id varchar(250),
    external_trigger boolean,
    end_date timestamp with time zone,
    start_date timestamp with time zone
);

CREATE TABLE validation_run_history (
    script_1 varchar(255),
    script_2 varchar(255),
    comp_operator varchar(10),
    test_result varchar(20),
    test_run_at timestamp
);
```

## Logging and Ingesting Performance Data

* ingest from the Airflow application database to the dag_run_history_table
* or use the Airflow REST API (if current versions deliver the required level of granularity)
* the data validator framework can be extended to log the result
* if you expect a large scale volume of logs, consider to use dedicated infrastructure (e.g. ELK or Splunk) instead of using the DWH directly

## Transforming Performance Data

* performance data can be captured by transforming the data collected above
* DAG success rate can be tracked by

```sql
CREATE TABLE IF NOT EXISTS dag_history_daily (
    execution_date DATE,
    dag_id VARCHAR(250),
    dag_state VARCHAR(250),
    runtime_seconds DECIMAL(12,4),
    dag_run_count int
);

TRUNCATE TABLE dag_history_daily;

INSERT INTO dag_history_daily
    (execution_date, dag_id, dag_state,
    runtime_seconds, dag_run_count)
SELECT
    CAST(execution_date as DATE),
    dag_id,
    state,
    SUM(EXTRACT(EPOCH FROM (end_date - start_date))),
    COUNT(*) AS dag_run_count
FROM dag_run_history
GROUP BY
    CAST(execution_date as DATE),
    dag_id,
    state;

SELECT
    dag_id,
    SUM(CASE WHEN dag_state = 'success' THEN 1
        ELSE 0 END)
        / CAST(SUM(dag_run_count) AS DECIMAL(6,2))
    AS success_rate
FROM dag_history_daily
GROUP BY dag_id;
```

* in order to avoid data becoming stale we may want to track the runtime change over time

```sql
SELECT
    dag_id,
    execution_date,
    SUM(runtime_seconds)
        / SUM(CAST(dag_run_count as DECIMAL(6,2)))
    AS avg_runtime
FROM dag_history_daily
WHERE
    dag_id = 'elt_pipeline_sample'
GROUP BY
    dag_id,
    execution_date
ORDER BY
    dag_id,
    execution_date;
```

* finally the test volume and success rate is given by

```sql
CREATE TABLE IF NOT EXISTS validator_summary_daily (
    test_date DATE,
    script_1 varchar(255),
    script_2 varchar(255),
    comp_operator varchar(10),
    test_composite_name varchar(650),
    test_result varchar(20),
    test_count int
);

TRUNCATE TABLE validator_summary_daily;

INSERT INTO validator_summary_daily
    (test_date, script_1, script_2, comp_operator,
    test_composite_name, test_result, test_count)
SELECT
    CAST(test_run_at AS DATE) AS test_date,
    script_1,
    script_2,
    comp_operator,
    (script_1 || ' ' || script_2 || ' ' || comp_operator) AS test_composite_name,
    test_result,
    COUNT(*) AS test_count
FROM validation_run_history
GROUP BY
    CAST(test_run_at AS DATE),
    script_1,
    script_2,
    comp_operator,
    (script_1 || ' ' || script_2 || ' ' || comp_operator),
    test_result;
```

## Orchestrating a Performance Pipeline

* the collection of this measuring data can be set up as a pipeline itself
* we define a DAG with steps
  * extract data from the Airflow database
  * load the Airflow extract into the DWH
  * transform the Airflow history
  * transform the data validation history

## Pipeline Transparency

* it's important to share the resulting insigths with your data team and stake holders to build trust and create a sense of ownership
* some tips to do so
  * leverage visualization tools
  * share summarized metrics regularly (at least monthly)
  * watch trends, not just current values
  * react to trends
