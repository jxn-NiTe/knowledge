# Data Ingestion: Loading Data

## loading data into Redshift DWH

* in production, use IAM authentication instead of simplified credentials from code samples
* load data from S3 into Redshift via COPY command (COPY table_name FROM source_file authorization)
* can be done directly from the Redshift Query Editor in the AWS console, but using again Python with the psycopg2 lib makes for a more standardized pipeline
* when using incremental loads, suggested to load data with no truncate and have all historical records, and then rely on timestamps when querying later
* when using CDC, add an EventType column to destination table so that delete records can be captured, not only insert or update

## loading data into a Snowflake DWH

* very similar to Redshift case, uses COPY INTO command
* Snowflake offers integration service Snowpipe to continually load data, instead of scheduling a bulk load based on COPY INTO
* use snowflake-connector-python lib

## using your file storage as a data lake

* data lake stores data in many formats (including raw or unstructured), cheap store, not optimized for querying
* good approach if dealing with lots of semi structured data (JSON) or being in exploration phase
* recently improved tooling to query data lake, e.g. AWS Athena

## open source frameworks

* since E and L steps can be repetitive, frameworks sprung up that provide core functionality and connections to common data sources and destination
* example Singer, uses taps to extract from source, streams in JSON to a target
* popular taps: Google Analytics, Jira, MySQL, PostgreSQL, Salesforce
* popular targets: CSV, BigQuery, PostgreSQL, Redshift, Snowflake

## commercial alternatives

* examples Stitch, Fivetran
* both cloud-hosted products, web-based, offering hundres of pre-built connectors usable without writing code
* include capabilities for orchestration, schema changes, handling duplicates etc.
* trade-offs to consider: cost, vendor lock-in, customization, security/privacy
