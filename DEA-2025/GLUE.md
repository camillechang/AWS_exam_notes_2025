**AWS Step Functions** is a fully managed service for building and orchestrating workflows across multiple AWS services. It integrates directly with AWS Glue and Amazon EMR, supports retries, error handling, wait states, and parallel execution. This makes it the best choice for automating ETL workflows with minimal manual effort.

**AWS Glue workflows** → Useful, but limited to AWS Glue jobs only. Since the company also uses Amazon EMR, Glue workflows cannot fully orchestrate the entire pipeline.

### Glue features

1. 数据发现与目录（Data Catalog）

- Glue Data Catalog：集中式的元数据存储，用于存放表、分区、模式(schema)信息，Athena、Redshift Spectrum、EMR 等服务都可以共享。

- Glue Crawler：自动扫描 S3、RDS、DynamoDB 等数据源，推断数据模式并在 Data Catalog 中创建或更新表结构。

- Schema Versioning：支持表 schema 的版本管理，方便溯源和兼容演进。

2. 数据集成与转换（ETL）

- Glue Studio：可视化 ETL 作业开发界面，拖拽式设计数据流，自动生成 PySpark/SparkSQL 代码。

- Glue Jobs：无服务器 ETL 作业（基于 Apache Spark），支持批处理大规模数据转换。

- PySpark / Scala：高级用户可直接写 Spark 代码。

- - Python Shell：轻量 ETL 脚本（适合小规模任务）。

- Glue DynamicFrames：对半结构化数据（JSON、Parquet）更友好的抽象，内置 schema 推断。Glue dynamic frame 提供 file-grouping 选项：
  - 会自动将大量小文件合并为较大的分区
  - 减少任务启动和 I/O 开销,在转换成 Parquet 并加载到 Redshift 时 显著提升吞吐量

Glue Transforms：内置常见数据清洗和机器学习预处理转换（如 FindMatches 做模糊去重）。

3. 数据流处理（Streaming ETL）

Glue Streaming Jobs：基于 Spark Structured Streaming，可直接消费 Kinesis Data Streams 或 Kafka，做实时清洗和转换后写入 S3、Redshift、OpenSearch 等。

4. 数据准备与探索（DataBrew）

Glue DataBrew：无代码数据准备工具（面向分析师）。

250+ 内置数据清洗/转换操作（去重、缺失值填补、格式转换）。

可直接可视化预览样本数据。

生成结果可导出到 S3 供 Athena/Redshift 使用。

5. 工作流与调度（Orchestration）

Glue Workflows：可以编排一系列爬虫、作业、触发器形成完整的 ETL 流程。

Glue Triggers：支持 定时调度（cron）或基于事件触发（如某个作业完成）。

与 Step Functions 集成：Glue Job 可嵌入复杂的分布式数据工作流。

6. 性能优化功能

- Job Bookmarking：自动追踪上次处理的偏移量，避免重复处理数据（增量加载场景）。

- Partition Pruning：与 Athena/Redshift 结合时，可以根据分区列裁剪数据，提高查询效率。

- Glue Data Catalog Indexing：对分区进行索引，加速分区过滤。

- Partition Projection（Athena 特性，Glue Catalog 配置）可减少元数据存储负担
