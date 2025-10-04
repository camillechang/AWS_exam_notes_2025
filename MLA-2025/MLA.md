 **Sagemaker**,
 - **Data Wrangler**,  provides a user-friendly interface to clean, preprocess, and transform data without needing to write custom code.
  - provides several built-in transformations to balance data, Random Oversampler/Undersampler and SMOTE(Synthetic Minority Over-sampling Technique)
- **Autopilot**, automating the process of building and deploying machine learning models. https://docs.aws.amazon.com/images/sagemaker/latest/dg/images/Autopilot-process-graphic-1.png
 - **Clarify**, helps identify potential bias during data preparation without writing code and explain predictions
 - **Debugger**, tools to register hookds to callbacks to extract model output tensors, built-in rules to detect model convergence issues, such as overfitting.Underutilized GPU,Vanishing / Exploding gradients
 - For Feature attribution drift,use the ModelExplainabilityMonitor class to generate a feature attribution baseline and to deploy a monitoring mechanism that evaluates whether the feature attribution has occurred. Then deploy the baseline to SageMaker Model monitor. https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html
 - **Shadow testing**, a feature that enables the testing of new machine learning (ML) models against production models using live data, without impacting the live inference traffic. This allows for the identification of potential configuration errors, performance issues, and other problems with a new model or model serving stack before it is fully deployed to production.
 - **Neo**, is a capability of Amazon SageMaker AI that enables machine learning models to train once and run anywhere in the cloud and at the edge.
 - **jumpstart**, ML hub with build-it models
 - **Ground Truth**, label workflows
 - **FSx for Lustre**,designed for large-scale ML training and HPC workloads
  - Can be linked directly to an S3 bucket, caching data as needed
  - Requires minimal setup
 - **ML Lineage Tracking**, creates and stores information about the steps of a machine learning (ML) workflow from data preparation to model deployment. With the tracking information, you can reproduce the workflow steps, track model and dataset lineage, and establish model governance and audit standards.
 - **Canvas**, import, prepare,transform,visualize and analyze data
 - Model Monitor provides the following types of monitoring:

    - Data quality - Monitor drift in data quality.

     - Model quality - Monitor drift in model quality metrics, such as accuracy.

     - Bias drift for models in production - Monitor bias in your model's predictions.

     - Feature attribution drift for models in production - Monitor drift in feature attribution.
 - SageMaker endpoints,can enable data capture and use that data for model re-training. https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-data-capture-endpoint.html
 - Bring your own containers in Sagemaker,for example, you have ML modesl build with R. https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-byoc-containers.html
 https://docs.aws.amazon.com/sagemaker/latest/dg/r-guide.html
- Sagemaker network isolation. This solution will block internet access and external network access.https://docs.aws.amazon.com/sagemaker/latest/dg/mkt-algo-model-internet-free.html
- **Asynchronous inference**,This option is ideal for requests with large payload sizes (up to 1GB), long processing times (up to one hour), and near real-time latency requirements. Asynchronous Inference enables you to save on costs by autoscaling the instance count to zero when there are no requests to process, so you only pay when your endpoint is processing requests.https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html
- batch transform, Run inference when you don't need a persistent endpoint https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html
- **real-time inference** supports payloads up to 5 MB for synchronous requests
- **Difference in proportions of labels (DPL)** is a metric that you can use to detect pre-training bias. You can use DPL to avoid ML models that could potentially be biased or discriminatory.https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-metric-true-label-imbalance.html
- **Partial dependence plots (PDPs)** illustrate how the predicted target response changes as a function of one particular input feature of interest. https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-processing-job-analysis-results.html#clarify-processing-job-analysis-results-pdp
-  **Shapley values** determines the contribution that each feature made to model predictions.  https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-shapley-values.html
- **SageMaker with TensorBoard**, provides full visibility into the model training process, including debugging and model optimization. This solution gives you the ability to debug issues, including lower than expected precision for a specific class. https://docs.aws.amazon.com/sagemaker/latest/dg/tensorboard-on-sagemaker.html
- **feature store**, Create a feature group. Ingest the records. Access the store to build datasets for training.https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store.html
- **managed warm pools** let you retain and reuse provisioned infrastructure after the completion of a training job to reduce latency for repetitive workloads, such as iterative experimentation or running many jobs consecutively
- **Inference Recommender**, reduces the time required to get machine learning (ML) models in production by automating load testing and model tuning
  -  helps you select the best instance type and configuration for your ML models and workloads. It considers factors like instance count, container parameters, model optimizations, max concurrency, and memory size.

**OpenSearch**, can use as  a Vector Database https://aws.amazon.com/opensearch-service/serverless-vector-database/

**Data augmentation** is the process of artificially generating new data from existing data, primarily to train new ML models. This method creates synthetic fraudulent cases and can help address the low number of fraudulent transactions. https://aws.amazon.com/what-is/data-augmentation/
  - Here are some of the benefits of data augmentation.
    - Enhanced model performance
    - Reduced data dependency
    - Mitigate overfitting in training data

** AppFlow** is a fully managed integration service that helps you securely transfer data between software as a service (SaaS) applications such as Salesforce, SAP, Google Analytics, Facebook Ads, and ServiceNow, and AWS services such as Amazon Simple Storage Service (S3) and Amazon Redshift in just a few clicks.
**Forecase**, handling missing values https://docs.aws.amazon.com/forecast/latest/dg/howitworks-missing-values.html

**Glue**

**DataBrew**, data quality rules, data cleaning and feature engineering.


**Lex** - chatbot, call center

**Polly** - text to speech

**Transcribe** - speech to text

**Forecast**- time-series forecasting model
**Rekognition**, primarily for image and video analysis (object detection, facial recognition) and is not the correct tool for converting audio or video speech into text.

**Comprehend**,uses a pre-trained model to examine and analyze a document or set of documents to gather insights about it. Use cases, sentiment/topic analysis
 -  can be used to detect and redact PII from user interactions.

**Kendra**, an intelligent enterprise search service, to traditional search solutions.
 - Kendra GenAI Index is a new index in Kendra designed for retrieval-augmented generation (RAG) and intelligent search to help enterprises build digital assistants and intelligent search experiences more efficiently and effectively.

**Comprehend**, service to build gen AI apps on AWS

**Bedrock**, Provides a fully managed API interface to Large Language Models (LLMs) like Jurassic-2.

**Amazon Managed Service for Apache Flink**, fully managed service that automatically scales and handles the underlying infrastructure for Apache Flink.
  - RANDOM_CUT_FOREST function's ability to detect anomalies is application-dependent

**Others**:
  - **embeddings**, High-dimensional vectors that contain the sematic meaning of text
  - Retrieval-Augmented Generation, **RAG**, enrichment of info from additional data to improve generated response
  - **temperature**, a hyperparameter that controls the randomness and diversity of a generative model's output by adjusting the probability distribution of the generated tokens. A low temperature sharpens the distribution, making the model's output more predictable and focused
  -**Top_k** limits the number of highest-probability next tokens the model can choose from.
    - Increasing the top_k expands the choices, introducing more diversity and randomness.
  -**recall**, focus on high false negative.
  -**precision**, focus on high False positive.
  - **concept drift**, when the statistical properties or patterns of the data an ML model is trained on change over time, causing the model's predictions to become less accurate or even incorrect.
  -**Mean absolute error (MAE)**, evaluating the performance of regression models. It quantifies the average magnitude of the errors between a model's predictions and the actual observed values.
  -**Learning Rate**, too high ⇒ overshoot, too small → take too long
  -** Trainium** chips are a family of AI chips purpose built by AWS for AI training and inference to deliver high performance while reducing costs.
**
**
**



** Performance metrics**
- Precision, recall, accuracy, F1 score, ROC, AUC, RMSE, MAPE
https://docs.aws.amazon.com/whitepapers/latest/aws-overview/machine-learning.html