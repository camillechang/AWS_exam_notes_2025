- **Airflow**
  - Orchestrates complex data pipelines with support for dependency management and scheduling.
  - Cost is relatively high (an Airflow cluster runs continuously and incurs fixed expenses), so it may not be the most cost-effective choice for simple ETL scenarios.
  - Open-source, cross-platform orchestration framework that can be deployed both on-premises and in the cloud.
  - With MWAA (Managed Workflows for Apache Airflow), you can host Airflow in the cloud while maintaining compatibility with on-premises Airflow DAGs.

- **Amazon Athena**
  - **Partition Projection**: Normally, Athena needs to enumerate all partitions from the AWS Glue Data Catalog before running a query. If you have thousands or millions of partitions, query planning time becomes a bottleneck. Partition Projection solves this by not storing partitions in Glue. Instead, Athena calculates partitions dynamically at query time based on rules you define.
  - **MSCK REPAIR TABLE**: This command scans the underlying paths in Amazon S3, detects new folders that represent partitions, and automatically adds them to the AWS Glue Data Catalog. This ensures Athena can query the most up-to-date data without manually adding partitions.
  - Athena vs S3 Select

- **Amazon EMR**
  - For terabyte-scale archived data, high-throughput, distributed processing (such as Spark or Hadoop) is required.
  - Amazon EMR is a mature and scalable choice that can process large volumes of data in parallel at once.

- **AWS Glue**

  - **AWS Glue workflows** → Orchestrates a series of crawlers, jobs, and triggers into a complete ETL pipeline。
  - **AWS Step Functions** is a fully managed service for building and orchestrating workflows across multiple AWS services. It integrates directly with AWS Glue and Amazon EMR, supports retries, error handling, wait states, and parallel execution.
  - **Glue DynamicFrames**,provides a higher-level abstraction for semi-structured data (JSON, Parquet) with built-in schema inference. DynamicFrames include file-grouping options:

    - Automatically merges many small files into larger partitions

    - Reduces job startup and I/O overhead, significantly improving throughput when converting to Parquet and loading into Redshift

  - **Glue DataBrew**, a no-code data preparation tool aimed at analysts. 250+ built-in data cleansing and transformation operations (deduplication, missing value filling, format conversion). Provides live visual previews of sample data.
   -**Glue Transforms**, built-in transformations for common data cleansing and ML preprocessing (e.g., FindMatches for fuzzy deduplication).
    -**Job Bookmarking**, automatically tracks the last processed offset to avoid reprocessing data (incremental load scenarios).
     -**Glue Studio**: a visual interface for designing ETL jobs. Drag-and-drop to create data flows, which automatically generates PySpark/SparkSQL code.

- **AWS Lake Formation**
  - Centralizes and secures S3-based data lakes, simplifies permissions, cataloging, and governance

- **Amazon Kinesis Data Firehose**
  - Fully managed service for loading streaming data into S3, Redshift, or OpenSearch
  - Can convert data formats, e.g., JSON → Parquet

- **Amazon Kinesis Data Streams**
  - Real-time streaming data ingestion and processing

- **Amazon Managed Service for Apache Flink**
  - Managed service for running Apache Flink applications for real-time stream processing

- **Amazon MSK (Managed Streaming for Apache Kafka)**
  - Fully managed Apache Kafka service for building streaming applications

- **Amazon OpenSearch Service**
  - Managed search and analytics service (formerly Amazon Elasticsearch Service)

- Amazon QuickSight,

  - **SPICE (Super-fast, Parallel, In-memory Calculation Engine)** is the in-memory data engine used by Amazon QuickSight.

    - **High performance**: Stores data in-memory to provide fast query and visualization responses.
    - **Parallel processing**: Can handle large datasets efficiently by distributing computations across multiple nodes.
    - **Scalable**: Automatically scales to support increasing data volume and concurrent users.
    - **Use case**: Ideal for interactive dashboards and analytics without waiting for live queries to complete.

- Redshift

  -  **Federated Query**, Allows direct querying of external Aurora PostgreSQL (or RDS/Postgres). This enables combining real-time transactional data with warehouse data during analysis without replicating all real-time data from the transactional database into Redshift. This approach retains real-time insights and reduces replication costs.
  -  **Query Editor v2**, A web-based interface that supports query scheduling.
  -  **materialized view** is a precomputed, stored version of a query result.
      - It improves query performance because the database can read from the stored result instead of recomputing it every time.
      - Useful for complex or frequently used aggregations.
      - Can be refreshed periodically to keep the data up-to-date.
    -  **Redshift Spectrum** allows Amazon Redshift to query data directly in **S3** without loading it into Redshift tables. - Works with data stored in formats like Parquet, ORC, JSON, or CSV.
    -  **Federated Query** enables Redshift to query **external databases** (like RDS, Aurora, or even MySQL/PostgreSQL) directly. - No need to move or copy data; queries run across Redshift and external sources.
    - **COPY Command**
    - Efficiently loads data from S3, DynamoDB, EMR, and Kinesis into Redshift
    - Supports parallel loading of multiple files (using manifest files)

  - **UNLOAD Command**
    - Exports Redshift tables to S3
    - Can be used as part of a data lake or as an intermediate step in ETL

  - **AWS Data Integration**
    - Glue ETL jobs can write directly into Redshift
    - DMS (Database Migration Service) can synchronize data from RDS or on-premises databases into Redshift

  - **TRUNCATE** in Redshift
    - A DDL operation that is more efficient than DELETE
    - Immediately reclaims storage space
    - Recommended for clearing tables or materialized views while recovering storage

- **Amazon DataZone** provides a fully managed data catalog and governance service with built-in support for business glossaries, custom metadata forms, and a user-friendly data portal. You can onboard your existing data assets, define glossaries, and capture business metadata without building or maintaining custom tables, APIs, or applications, minimizing operational overhead.
