# Common Data Pipeline Patterns

## ETL and ELT

* both widely used in DWH and BI
* difference is order of steps, with substantial design implementations
* extract = gather data from various sources in preperation of loading and transforming
* load = bring raw data (ELT) or fully transformed data (ETL) into the final destination (DWH, data lake or other)
* transform = combine and format data in a way useful for analysts or visualization tools
* E and L are referred to as data ingestion, and usually packaged together in software frameworks, but should be considered separate steps

## The emergence of ELT over ETL

* in the past, DWH didn't have compute or storage necessary to handle transformation in place
* row-based database good for transactional use-case, less for high-volume bulk queries needed in today's analytics
* today's DWH built on scalable, columnar databases, good for bulk transforms on large datasets, with good I/O efficiency and distributable across nodes => sensible to EL first to DWH and T from there
* use case for row-based: e-commerce web app, likely to query or update one order at a time frequently, more important than disk inefficiency due to storing records in blocks
* in analytics, situation reversed: r/w large amount of data infrequently, often times require not all columns of a table, e.g. analyze orders in bulk looking for customer patterns
* columnar databases are more disk efficient by fully utilzing blocks and optimally compressing (homogeneous data)

## EtLT subpattern

* t in EtLT captures transformations that are still useful to do between E and L, but more lightweight and require no business logic or serve compliance reasons, e.g.
  * deduplicate records
  * parse URL parameters into individual components
  * mask sensitive data

## ELT for data analysis

* since analysts are familiar with SQL, ELT allows for clear separation: data engineers can focus on ingestion and analysts on transformation, i.e. team members focus on their strength with less coordination and more autonomy

## ELT for data science

* requirements for scientists similar to analysts, but less dashboards and metrics and more granular data feeding models, so the E and L part largely remain the same

## ELT for data products and machine learning

* Examples of data products likely powered by ML models: content recommendation engine for video streaming, personalized search engine on e-commerce website
* training and validation required for ML likely to come from different sources that require transfomration, so ELT is well suited
* ML pipelines begin similar to analytics pipelines, but the transform step does not focus on data modeling
  * ingestion, where additionally ingested data is versioned so you can refer to specific datasets later
  * preprocessing, e.g. tokenize text, convert features to numerical values, normalize values
  * model (re-)training
  * model deployment, also needs versioning with different API endpoints for each
* ML pipelines also need to gather feedback for model improvements, e.g. by some event collection (e.g. what recommendations were clicked and enjoyed afterwards) that gets ingested back to the DWH so effectiveness of a model can be measured
