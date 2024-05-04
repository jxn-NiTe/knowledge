# A Modern Data Infrastructure

## diversity of data sources

* typically, ingest data from both internal sources and third parties (e.g. e-commerce company takes shopping cart data from own database and google analytics for website traffic data)
* understanding source ownership is important to understand data accessibility and design pipelines
* common interfaces
  * database
  * REST API
  * stream processing (e.g. Kafka)
  * files (CSV, logs, flat file) in network or cloud bucket
  * DWH / data lake
* common structures include JSON, structured data, CSV, flat files and bring different transformation challenges
* high volume does not imply high value
* "garbage in, garbage out" due to messy data (duplicate/orphaned/incomplete/missing/mislabeled data, encoding and consistency issues etc.) requires a strategic approach
  * assume the worst, expect the best
  * clean and validate in the system best suited to do so
  * validate often
* source system will impose latency or bandwidth limits

## cloud data warehouses and data lakes

* major cloud providers introduced
  * easy build and deploy of pipelines, DWH and analytics processes
  * storage
  * scalable, columnar databases (Redshift, Snowflake, Big Query)
* which together leads to the data lake concept
* DWH = dabase with data from different systems, modeled to support analysis, structured and optimized for reporting
* data lake = storage without structure or query optimization, high volume and variety

## data ingestion tools

* common examples: Stinger, Stitch, Fivetran
* build or buy trade-offs (see chapter 5)
* data ingestion includes the extract (from source) and load (to destination) steps from ETL or ELT
* some tools can also do transformation steps, but in practice many like to keep it separate from ingestion

## data transformation and modeling tools

* transformation = T in ETL / ELT, can be simple (convert a timestamp) to more complex (aggregate and filter multiple columns to single metric)
* data modeling = defines data in a format optimized for analytics, usually tables in a DWH
* example of transformation that can be handled by an ingestion tool, turn mail address into hash value to comply with PII protection
* more specialized or context-dependent transformation can be written in Python or SQL, or handled by a specialed tool like dbt
* data models are typically defined in SQL or in no-code tools, usually SQL to be prefered

## workflow orchestration platforms

* with increasing number and complexity of pipelines a dedicated workflow orchestration platform becomes more attractive than cron scheduled scripts
* they are based on DAGs (directed acyclic graphs)
* examples: Airflow, Luigi, AWS Glue
* the orchestrator executes each task, the task logic itself exists usually as SQL or Python code

## customizing your data infrastructure

* most organizations pick and choose tools and vendors that fit their specific need and build the rest on their own
* as always in build-or-buy, you need to understand the constraints and weigh the trade-offs
