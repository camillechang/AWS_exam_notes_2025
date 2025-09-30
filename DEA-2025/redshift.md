

### 核心功能

#### 1 数据仓库和架构特性

- **列式存储**
  数据按列而非行存储。

  - **优点**: 适合大规模分析、聚合查询，扫描更少的列 → 提高查询性能，降低 I/O 成本。

- **大规模并行处理 (MPP)**
  支持单个主节点和多个计算节点。

  - **优点**: 将数据分布到各节点进行并行计算，提高吞吐量。

- **数据分布策略**

  - **KEY 分布**: 根据列值分布数据 → 避免跨节点数据混洗。
  - **EVEN 分布**: 均匀分布数据 → 适合小表或无关联列。
  - **ALL 分布**: 将小表复制到每个节点 → 避免频繁广播。

- **排序键**
  数据按指定列排序 → 查询时跳过无关块（区域映射）。
  - **优点**: 优化范围扫描、聚合和 JOIN 操作。

### 2 查询和分析特性

#### 标准 SQL 支持

- **完整 ANSI SQL 支持**
- 支持复杂 JOIN、窗口函数、子查询
- **并行查询（MPP）**
  - Redshift 自动将 SQL 查询拆分到各节点并行执行

#### 物化视图（Materialized Views）

- 缓存复杂聚合查询结果
- 加速频繁查询的报表

#### Redshift Spectrum

- 查询 S3 上的数据（Parquet、ORC、CSV、JSON 等）
- 无需先加载到 Redshift → 数据湖分析

#### 查询优化

- **自动统计信息（ANALYZE）**
- **并行执行计划（EXPLAIN/EXPLAIN ANALYZE）**

### 3 数据加载与集成

- **COPY 命令**
  - 高效加载 S3、DynamoDB、EMR、Kinesis 数据
  - 支持并行加载多文件（Manifest 文件）
- **Unload 命令**
  - 将 Redshift 表导出到 S3
  - 可作为数据湖 / ETL 中间环节
- **AWS 数据集成**
  - Glue ETL 作业直接写入 Redshift
  - DMS 可将 RDS / On-prem 数据同步到 Redshift
- **TRUNCATE** 在 Redshift 是 DDL 操作，比 DELETE 更高效，能立刻回收空间。是清空表/物化视图并回收存储的首选


### Others
**Federated Query**
Allows direct querying of external Aurora PostgreSQL (or RDS/Postgres). This enables combining real-time transactional data with warehouse data during analysis without replicating all real-time data from the transactional database into Redshift. This approach retains real-time insights and reduces replication costs.

**Query Editor v2**
A web-based interface that supports query scheduling.
**SUPER 类型**是一种用于存储和处理半结构化数据（semi-structured data）的数据类型，比如 JSON、Avro、Parquet、ION 等。它允许你在 Redshift 中直接存储复杂的数据结构，而无需事先展开成关系型表。