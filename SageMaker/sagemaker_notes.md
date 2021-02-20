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
  * Create an AWS account
    * This is needed for billing and access to all resources
    * This is also called the root user
  * Create and IAM Administrator User and Group
    * The account allows access to all AWS resources, as such it is recommended to set up administrators and lock away the primary account for only the highest level functions
  * Onboard users
    * SageMaker console allows for either SSO or IAM users to be onboarded
    * Simplest method is to use the Quick Start procedures
    * SSO has a couple benefits over IAM
      * Members have a unique sing-in URL that directly opens Studio while IAM requires the SageMaker console
      * Organizations can manage members in SSO instead of SageMaker Studio
    * Return to [documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/onboard-quick-start.html) to see the onboarding steps based on the method
    * Choose a VPC
      * By default, SageMaker uses a VPC for internet access and another for encrypted traffic between the domain and EFS volume
      * It is possible to change this so all traffic can be sent over a single VPC
        * This will require the subnets, security groups, and interface endpoints
    * Delete a Domain
      * In order to reset to pre-onboarding you must delete the created domain
  * SageMaker JumpStart is a collection of solutions, models, algorithms and example notebooks designed for onboarding
* SageMaker Studio
  * Web-based, IDE for machine learning that allows for building, training, debugging, deploying, and monitoring models
  * UI Overview
    * Extension of the JupyterLab interface
    * Top section is the menu bar
    * Left section is the left sidebar
      * File Browser
      * Running Terminals and Kernels
      * Git
      * Commands
      * Notebook Tools
      * Open Tabs
      * SageMaker JumpStart
      * SageMaker Components and Registries
    * Right sectino is the right sidebar
    * Left pane is the file and resource browser
    * Right pane is a space for tabs for resources like notebooks, terminal, metrics and graphs
  * Studio Launcher
    * Can be used to start notebooks and text files, launch terminals and interactive Python shells
  * Studio Notebooks
    * Designed to be collaborative and launched quickly
    * Fast launch types are designed to launch in less than two minutes
    * Notebooks provide persistent storage even when instances are shut down
    * You can also provide read-only URLs to other users
    * Notebooks run in an environment defined by:
      * EC2 instance type - hardware resources
      * SageMaker image - container image that consists of kernels, language packages and other files
      * KernelGateway - image runs as a KernelGateway app
      * Kernel - process that inspects and runs the code in the notebook, which contains a kernel spec
  * Studio Notebooks vs. Notebook Instances
    * It is recommended to use the Studio instead of the console
      * Studio start up is faster (5-10 times)
      * Notebook sharing is an integrated feature
      * Come pre-installed with the latest Python SDK
      * Accessed from within the Studio, which speeds up other functions
      * Each member gets their own home directory and EFS mount
      * When using SSO you can go direct to the Studio
      * Equipped with a set of predefined image settings
  * Create or Open a Notebook
    * CPU based images default to an ml.t3.medium instance
    * GPU based images default to an ml.g4dn.xlarge instance
    * You can only have one instance of each instance type running, but each image can run multiple kernels or terminal instances
  * Use the Toolbar
    * Save and checkpoint
    * Insert cell
    * Cut, copy, and paste cells
    * Run cells
    * Interrupt kernel
    * Restart kernel
    * Cell type
    * Launch terminal
    * Checkpoint diff
    * Git diff
    * Instance type
    * Kernel and SageMaker Image
    * CPU and memory of the kernel or instance
    * Kernel busy status
    * Share notebook
  * Share and Use a Notebook
    * 