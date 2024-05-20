# Data Validation in Pipelines

## validate early, validate often

* detecting data quality issues at the end of a pipeline having to trace it back is a highly undesirable situation
* data engineers can't be expected to have enough context to validate every dataset, but they can set the stage by leading with noncontextual validation and provide templates for more specific validation
* why we can't assume that source systems contain only valid data?
  * invalid data may not impact the functioning of the source system itself
  * source system may function fine when records are orphaned
  * unknown or unfixed bug may exist in source system
* ways how the ingestion itself can go wrong
  * outage or timeouts during extract or load step
  * logical errors in incremental ingestion (e.g. >= vs >)
  * parsing issues in an extracted file (e.g. encoding issues)
* how to enable validation by data analysts (who understand business context best)
  * empower them with a reliable method of writing and executing validation tests

## a simple validation framework

* general concept: python script that executes a pair of SQL scripts and compares
* e.g. count rows in table for given day and previous day and assert that the current day has >= than previous day
* example code uses the pipeline.conf file from before and the psycopg2 to access a Redshift DWH
* using command line arguments, tell validator to executue specific pair of SQL scripts and comparison operator, and use the return pass/fail value in the DAG flow
* example `$ python validator.py order_count.sql order_full_count.sql equals`
* when to halt and when to warn and continue the pipeline?
  * in general, stale data better than incorrect data
  * sometimes failure less critical, more informational (e.g. table size increased more than daily average)
  * based on business context and use case of data => need for both engineers and analysts being empowered to contribute
* ideas to extend the framework (closer towards production readiness)
  * send slack messages for immediate feedback
  * exception handling (e.g. invalid command line args)
  * run multiple tests with a single execution of the validation script

## validation test examples

* checking for duplicate records after ingestion
* e.g. select 0 vs select count(*) from CTE where we group by id having count > 1
* unexpected row count after ingestion
* e.g. using a two-tailed test with some threshold
* metric value fluctuations after transformation -- check a metric is within bounds, row count growth, unexpected fluctuation in the value of a particular metric
* e.g. use a z-score on daily revenue
