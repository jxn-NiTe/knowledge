# Best Practices for Maintaining Pipelines

## Handling Changes in Source Systems

* source systems are not static
* whenever possible, introduce layer of abstraction between source system and ingestion process
  * e.g. don't query from database directly, but use a REST API that pulls from the database (or use a Kafka topic)
  * creates awareness of the need to handle change
* maintain a data contract, i.e. written agreement between data producer and consumer covering following aspects
  * what data is extracted and how
  * contact person
  * semantics
  * data quality expectations
  * written in standardized format (e.g. yaml) so it can be part of CI/CD
  * can develop automtated tooling around contract, e.g. quality checks or git hook to detect breaking changes
* consider moving from schema-on-write design to schema-on-read
  * schema-on-write: used so far in chapters 4-5, data is loaded into a defined table structure
  * schema-on-read: write data to data lake or S3 bucket with no strict schema, i.e. schema only becomes known when it's read
  * when using schema-on-read, use a data catalog (e.g. AWS Glue Data Catalog or Apache Atlas) to store metadata for the data set and focus on data governance
  * increases complexity in load step (add new columns on the fly? how to notify?)

## Scaling Complexity

* pipeline maintenance challenging due to variety of source system types
* if ingesting from internal systems, try to collaborate with other engineering teams and aim for standardization
* if ingesting from third parties, try to be part of the evaluation process early
* standardize whatever code you can, and reuse
* strive for config-driven data ingestions
  * don't write a different job for each Postgres ingestion but rather single job that iterates through config files)
* consider your own abstractions
  * if source system owner doesn't build standardized abstraction, consider doing so yourself
* in data modeling, trade-off between code reuse and more complex dependency graph
  * e.g. when loading order data, build 4 independent models or build an order_by_day model that is used by further downstream models?
  * write logic once and then reuse creates a single source of truth
* keeping track of model dependencies can be time consuming and error prone and thus should be handled programmatically, e.g. by a dedicated framework like dbt
