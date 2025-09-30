**Kendra**, an intelligent enterprise search service, to traditional search solutions.
 - Kendra GenAI Index is a new index in Kendra designed for retrieval-augmented generation (RAG) and intelligent search to help enterprises build digital assistants and intelligent search experiences more efficiently and effectively.

**Comprehend**,uses a pre-trained model to examine and analyze a document or set of documents to gather insights about it.
 -  can be used to detect and redact PII from user interactions.

 **Sagemaker**,
 - For Feature attribution drift,use the ModelExplainabilityMonitor class to generate a feature attribution baseline and to deploy a monitoring mechanism that evaluates whether the feature attribution has occurred. Then deploy the baseline to SageMaker Model monitor. https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html
 - Model Monitor provides the following types of monitoring:

    - Data quality - Monitor drift in data quality.

     - Model quality - Monitor drift in model quality metrics, such as accuracy.

     - Bias drift for models in production - Monitor bias in your model's predictions.

     - Feature attribution drift for models in production - Monitor drift in feature attribution.
 - SageMaker endpoints,can enable data capture and use that data for model re-training. https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-data-capture-endpoint.html
 - Bring your own containers in Sagemaker,for example, you have ML modesl build with R. https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-byoc-containers.html
 https://docs.aws.amazon.com/sagemaker/latest/dg/r-guide.html
- Sagemaker network isolation. This solution will block internet access and external network access.https://docs.aws.amazon.com/sagemaker/latest/dg/mkt-algo-model-internet-free.html
- Asynchronous inference,This option is ideal for requests with large payload sizes (up to 1GB), long processing times (up to one hour), and near real-time latency requirements. Asynchronous Inference enables you to save on costs by autoscaling the instance count to zero when there are no requests to process, so you only pay when your endpoint is processing requests.https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html
- batch transform, Run inference when you don't need a persistent endpoint https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html
- **Difference in proportions of labels (DPL)** is a metric that you can use to detect pre-training bias. You can use DPL to avoid ML models that could potentially be biased or discriminatory.https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-metric-true-label-imbalance.html
- **Partial dependence plots (PDPs)** illustrate how the predicted target response changes as a function of one particular input feature of interest. https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-processing-job-analysis-results.html#clarify-processing-job-analysis-results-pdp
-  **Shapley values** determines the contribution that each feature made to model predictions.  https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-shapley-values.html



**OpenSearch**, can use as  a Vector Database https://aws.amazon.com/opensearch-service/serverless-vector-database/