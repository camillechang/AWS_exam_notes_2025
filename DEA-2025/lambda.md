**Lambda** is fully managed and integrates seamlessly with API Gateway.
| Mode                        | Latency       | Cost Impact                       | When to Use                                  |
| --------------------------- | ------------- | --------------------------------- | -------------------------------------------- |
| **Cold Start**              | 100ms–seconds | You pay for init time + execution | Occasional or non-latency-critical workloads |
| **Warm / Normal Lambda**    | Minimal       | Only pay for execution time       | Occasional or unpredictable workloads        |
| **Provisioned Concurrency** | Minimal       | Hourly cost + execution cost      | High-frequency, latency-sensitive workloads  |
**Amazon S3 Object Lambda** Access Points can be leveraged to dynamically manage Personally Identifiable Information (PII) within data stored in Amazon S3