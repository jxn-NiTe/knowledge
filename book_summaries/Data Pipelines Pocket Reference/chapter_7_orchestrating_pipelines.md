# Orchestrating Pipelines

* pipeline steps (tasks) are always directed, guarenteeing a path of execution with no dependencies missed, in essense a DAG (directed, acyclic graph)

## Airflow setup and overview

* open source project to solve common challenge how to build, manage and monitor workflows
* built in Python, but can execute tasks in any language or platform
* comes with web interface, cli and built-in scheduler
* uses a database to store metadate related to execution history, SQLite by default but easily replacable by others that work with Sql Alchemy, e.g Postgres (recommended)
* interaction with Postgres from Python via psycopg2 lib
* comes with different executors (e.g. for Celery, Dask, Kubernetes), choose based on infrastructure you are comfortable with
* each task is executed by a operator, including ones for Bash, Python, Http, Email, Slack, Databases
* DAGs are defined in Python scripts

## building Airflow DAGs

-> see sample code

## additional pipeline tasks

* options to send notifications when a DAG or particular task fails
* can be done via mail, slack or handrolled from Python or bash

## advanced orchestration configuration

* streaming pipelines are more complicated than batch pipelines
* e.g. Kafka streams to S3 bucket, from where it's continuously loaded into Snowlake via Snowpipe, but transformation step scheduled in 30 min interval, leading to uncoupled taks
* key decision point: what tasks belong together and which should be split up, some guidelines:
  * if tasks require different schedules, break into multiple DAGs
  * when pipeline is truly independent, keep it separate
  * when DAG becomes too complex, determine whether you can break it out logically
* airflow has special sensor operator to coordinate different DAGs with shared dependencies
* alternatively to self-hosting, Airflow can be used as a managed service

## other orchestration frameworks

* general orchestration: Luigi, Dagster
* geared towards ML: Kubeflow Pipelines
* orchestration of transformation steps: dbt
