# Data Ingestion: Extracting Data

## setting up your Python environment

* use configparser lib to read configuration info, but don't add to git to not expose credentials

## setting up cloud file storage

* use AWS S3 bucket (5 GB free storage for first 12 months) with AWS Identity and Access Management (IAM)
* use boto3 lib to interact from Python with the bucket
* sample pipeline.conf file

## extracting data from a MySQL database

* supposes some orders table to exist, e-commerce context
* full extraction approach (full select without filtering) least complex, but can take long on high-volume tables
* in full extraction approach, usually truncate destination table before load step
* incremental extraction (select ... where LastUpdated > timestamp) can be achieved by storing last extraction timestamp in a job log table or querying the max(LastUpdate) from the destination table
* incremental more performant but requires reliable timestamp information and misses deleted rows
* in incremental approach, usually append records to destination table
* MySQL can be accessed from Python via pymsql lib
* another approach is to use the MySQL binlog which keeps a record of every operation performed in the DB (a form of change data capture (CDC))
* efficient method for high-volume ingestion
* involves steps
  * enable binlog on MySQL server
  * run initial full table extract and laod
  * extract from binlog on continuous basis
  * translate and load binlog extracts into DWH (e.g. as CSV file)
* binlog events can be retrieved with the mysql-replication lib

## extracting data from a PostgreSQL database

* table extraction similar to MySQL, but uses pyscopg2 lib instead
* CDC-based method for Postgres is to use the write-ahead log (WAL) in conjunction with Debezium

## extracting data from MongoDB

* supposes existing documents that represent event logs from a webserver, each containing a timestamp and some properties to extract
* uses the pymongo lib
* good practice to include default values in `doc.get()` calls, since document data is unstructed and there is no guarantee fields are always present

## extracting data from a REST API

* common source for external services, following the usual pattern of
  * send HTTP GET yo API endpoint
  * accept JSON formatted respone
  * parse response and flatten into CSV if needed (some DWH can handle JSON directly)
* uses requests lib

## streaming data ingestions with Kafka and Debezium

* Debezium bundles open source services to capture CDC systems and stream them as consumable events
  * Zookeper, handles distributed environment and configuration
  * Kafka, streaming platform organized into topics to which you can publish or subscribe
  * Kafka Connect, pre-built connectors to connect Kafka to (including most common databases)
