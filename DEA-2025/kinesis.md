| 特性       | Kinesis Data Streams (KDS) | Kinesis Data Firehose               |
| -------- | -------------------------- | ----------------------------------- |
| **实时性**  | 毫秒级到秒级                     | 秒级到分钟级（缓冲批量传输）                      |
| **数据存储** | 临时存储（1–7天）                 | 不存储，只缓冲                             |
| **消费者**  | 多个并行消费者，需自己管理              | 内置目标（S3、Redshift、Splunk 等），不可多路并行消费 |
| **可扩展性** | 需要管理 shards（分片）            | 自动扩缩容                               |
| **运维开销** | 高（要写 consumer、管 shard）     | 低（全托管）                              |
| **典型场景** | IoT 实时分析、风控、推荐系统           | 日志收集、数据湖落盘、数据归档、监控数据送 Splunk/ELK    |

简单判断：

- 如果你要 实时处理（sub-second）+ 多消费者 → 用 Data Streams。
- 如果你要 近实时收集/落盘，直接送到 S3/Redshift/Splunk → 用 Firehose。


### Firehose
1. convert the format json->parquet