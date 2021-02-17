# SageMaker 

- [SageMaker](#sagemaker)
  - [Developer Guide](#developer-guide)

## Developer Guide 
[Developer Guide](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html)
* What is Amazon SageMaker?
  * Fully managed machine learning service
  * Tools to build, train and deploy models into production
  * Built on Jupyter notebooks
  * Provides optimized algorithms and bring-your-own-algorithms
  * Billed by minutes of usage and instance size
  * Typical workflow
    * Generate example data
      * Fetch the data
      * Clean the data
      * Prepare or transform the data
    * Train a model
      * Training the model
      * Evaluating the model
    * Deploy the model
  * Data processing
    * SageMaker has tools for handling the processing, both pre- and post-, andcan even be run in [containers](https://docs.aws.amazon.com/sagemaker/latest/dg/build-your-own-processing-container.html)
  * Fairness and Model Explainability
    * SageMaker Clarify
      * Provides tools for detecting bias and feature attribution drift
    * This is to meet regulatory and business needs
    * Can also be used for debugging and improvement through feature engineering
    * Best practices
      * Fairness as a Process
        * Consider how fairness is measured and gain consensus amongst shareholders
      * Fairness and Explainability by Design
        * Consider these features in each aspect of the lifecycle
    * Some samples are also provided:
      * [Bias Detection](https://github.com/aws/amazon-sagemaker-examples/blob/master/sagemaker_processing/fairness_and_explainability/fairness_and_explainability.ipynb)
      * [Drift](https://github.com/aws/amazon-sagemaker-examples/blob/master/sagemaker_model_monitor/fairness_and_explainability/SageMaker-Model-Monitor-Fairness-and-Explainability.ipynb)
  * Model Training
    * To train a model you create a training job, which contains:
      * URL of S3 bucket
      * Computer resources
      * URL of S3 output
      * Elastic Container Registry where the training code is stored
    * Many tools to help train
      * Algorithms provided by SageMaker itself
      * Debugger for tools like TensorFlow and PyTorch
      * Apache Spark
      * Custom code
      * Custom algorithms
      * AWS Marketplace
  * Model Deployment
    * Can setup a persistent endpoint for single prediction or a batch transform for full datasets
    * To deploy:
      * Create a model in SageMaker
        * Must contain S3 path for model artifacts and Docker registry for inference code
        * Create an endpoint for HTTPS
    * Best practices
      * Consider the request sender (client app or Jupyter notebook for instance)
      * Deployments can be pushed to whatever target you wish
      * You can deploy multiple variants to the same endpoint
      * Endpoints can be configured to autoscale
      * You can modify an endpoint without taking models out of service
      * Deleting or changing model artifacts or inference code can have unexpected consequences
      * Consider batch transforms for running inferences on full datasets
  * Batch Transform
    * Stores output into S3 bucket
    * Manages the compute resources automatically (including launching and deleting instances)
    * Can be used when:
      * You want inferences indexed for real time serving
      * Don't need a persistent endpoint for apps
      * Dont' need subsecond latency like in hosted endpoints
    * Can also be used to preprocess data
  * Validating Models
    * Can evaluate with offline testing (via Jupyter for instance) or live data (online testing, production variants)
  * Model Monitoring
    * Model monitor is [built-in](https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html)
    * CloudWatch Logs collect log files and model status into S3
  * Supported Regions and Quotas
    * [Pricing](http://aws.amazon.com/sagemaker/pricing/)
    * [Endpoint Quotes](https://docs.aws.amazon.com/general/latest/gr/sagemaker.html)
* Get Started
  * 