**Athena partition projection**, Normally, Athena needs to enumerate all partitions from the AWS Glue Data Catalog before running a query. If you have thousands or millions of partitions, query planning time becomes a bottleneck.Partition Projection solves this by not storing partitions in Glue. Instead, Athena calculates partitions dynamically at query time based on rules you define.
  - Best suited for:
  - - Very large numbers of partitions (hundreds of thousands to millions).
  - - Partition values that follow predictable patterns (like year=YYYY/month=MM/day=DD).
在正常情况下，Athena（和 Glue Data Catalog）需要 列举所有分区 才能执行查询，分区越多，查询规划时间就越慢。
Partition Projection 则让分区元数据 不再存储在 Glue 中，而是根据 规则（模式）在查询时动态推算，这样 Athena 不需要扫描 Glue 的所有分区，直接减少 planning 时间。

在 Amazon Athena (基于 Presto/Trino 引擎) 里：
  - EXPLAIN <query> → 只会输出 逻辑执行计划，不会真正执行 SQL。
  - EXPLAIN ANALYZE <query> → 会真正执行 SQL，并输出执行计划 以及每个步骤的实际运行统计信息（包括计算代价、处理的行数、时间消耗等）。

Athena vs S3 select:
| 特性     | **S3 Select** | **Athena**              |
| ------ | ------------- | ----------------------- |
| 查询范围   | 单个对象内部        | 跨多个对象/表                 |
| SQL 能力 | 基础 SQL 子集     | 完整 SQL（JOIN、聚合、窗口函数）    |
| 成本     | 更低，适合小规模、单文件  | \$5/TB 扫描，适合大规模分析       |
| 性能     | 低延迟，直接取结果     | 适合大批量、复杂查询              |
| 使用门槛   | 无需建表，直接查询文件   | 需要 Glue Data Catalog 建表 |
| 典型场景   | 临时抽查/审计单文件    | 数据湖分析、报表、BI 查询          |

-**MSCK REPAIR TABLE**, Amazon Athena 中用于 修复分区表 的 SQL 命令。它的作用是扫描 S3 中表的底层路径，根据文件夹结构自动添加新分区到 AWS Glue Data Catalog，以便 Athena 可以查询最新的数据