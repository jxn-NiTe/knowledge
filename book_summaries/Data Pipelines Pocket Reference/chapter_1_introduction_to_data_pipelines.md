# Introduction to Data Pipelines

## What are data pipelines?

* set of processes that move and transform data from various sources to a destination where new value can be derived
* foundation of analytics, reporting, ML
* complexity can range from simple, e.g. extract from single source and load to SQL table...
* ...to multiple steps including extraction, preprocessing, validation, running a ML model, which can be scattered across different systems

## Who builds data pipelines?

* increase in both number of data sources (cloud computing and SaaS) and demand for data to feed ML and data science research, led to the emergence of data engineering
* data engineers specialize in building and maintaining
the data pipelines that underpin the analytics ecosystem
* close collaboration with data scientists / analysts to help bring their needs into a scalable production state (e.g. timeliness, validity, testing, alerting for data deliveries)
* specific skills depend on organization's tech stack, but good to have
  * SQL, Databases, DWH, data modeling
  * Python, Java (most widespread in the domain)
  * distributed computing frameworks (e.g. Hadoop, Spark)
  * basic system administration (logs, scheduling, security)
  * mentality to understand stakeholder's needs which in turn informs architecture decisions

## Why build data pipelines?

* shiny toys (dashboards, analytics insights etc.) need to derive from quality data, which includes multiple sources, cleansing, normalizing, aggregating, sometimes anonymizing

## How are pipelines built

* fragmented tooling: open source vs commercial vs in-house, different languages, cloud vs on-prem
* book will try to cover the most popular ones and how to consider which
* pipelines are not build-once, but need maintenance, monitoring and supporting infrastructure
