#  MLflow: A Machine Learning Lifecycle Platform
## ML Lifecycle Challanges
* Portability: Machine Learning end to end development and deployment is complex and considering non-determinstic nature of the subject it become more important to 
  straterzie appropiately for intergating it to the business and our products. Moving a model to production can be challenging due to the plethora of deployment 
  tools and environments it needs to run in (e.g. REST serving, batch inference, or mobile apps). There is no standard way to move models from any library to any 
  of these tools, creating a new risk with each new deployment.

* Compartibility: Data scientists build the models on different tools and make use of different packages and libraries. When these packages or libraries are 
  updated prior deployed models become in-compitent with the latest deployed environment. This casues the failure of the deployed models. 

* 100s of software tools to leverage , No Model Management/Tracking. ( Hard to track & reproduce results - code, data ,params and metrics , Hard to Productionize 
  models. Deployment require re-write from data scientists to software Engineers. Restrict model complexity to simplify model deployment.
  
* ML development brings many new complexities beyond the traditional software development lifecycle. Unlike in traditional software development, ML developers want 
  to try multiple algorithms, tools and parameters to get the best results, and they need to track this information to reproduce work. In addition, developers need 
  to use many distinct systems to productionize models. To address these problems, many companies are building custom "ML platforms" that automate this lifecycle, 
  but even these platforms are limited to a few supported algorithms and to each company's internal infrastructure. 

### CUSTOM ML Platforms Vs MLFlow: 
* Uber’s - Michelangelo; Facebook-FBLearner Flow and Google - TFX (Vs MLFlow)
* These platforms are very powerful - Standardize the data prep/training/deployment cycle. As long you work within APIs in these platforms you get the application 
  or pipeline which can be modified and applied very easily. Its good idea to develop ML Platform
* Every Platform is limited to few algorithms and frameworks.
* Each platform is very my customized around the infrastructure of these companies so there is no sharing of common work around it.
* MLFLOW helps here to integrated end to end ML Pipeline in "OPEN" Manner. (Open Standard)
  * MlFlow Tracking - Experiment Tracking
  * MLFlow Projects - Reproduciable Runs
  * MLFlow Models - Model Packaging
  * Runs teh same way anywhere : on-prem or any cloud
  * Zero code refactor between research ready models and production deployments
  
##  Machine Learning Pipeline Development is Complex !! Why??

### WHY ML is HARD to OPERATIONALIZE?
* Dependency on Data. ML needs new data, consistent. (Challabges of maintaining the date pipeline have to be solved to do MLOps).
* Data Drift - Data is changing or verions of the deployment is different from the version in prod.
* Monitoring Preformance of the Model, Governance and Security. 
* Teams spending more that >50% for maintaining the existing models instead of building new one for new use cases.
* Every team's requirement is different and change overtime. 

### ML Pipeline Stages/Phases !!
* DATA Gathering. 
* DATA Analysis : What variables we can use and what variables we cannot use.
* DATA PRE-PROCESSING: During feature engineering, we transform the variable to make them useful in the machine learning models, filling missing values etc.
* FEATURE Selection: Why we need to select feature in first place? Feature selections means finding those variables which are most predictive one and building the 
  models around those variables.
* MODEL BUILDING: Typically build various ML algos and choose the ones which give the best results. 
* UPLIFT IN Business Value: Model bring the actual business value.
* MODEL DEPLOYMENT
* Different aspects: Data Science (typically - data preperation, experiment phase - Statistical analysis, train and  data build model. Creating and registering the 
  model's central repo- file system, git hub or docker registery and create image out of it). ;Deployment ; Model Serving and Model Monitoring.

![image](https://user-images.githubusercontent.com/13011167/92307830-c071ef00-efb6-11ea-98d8-ce107a957ff0.png)

# GETTING STARTED WITH MLFLOW 
## MLflow: A Machine Learning Lifecycle Platform

### MLflow designed to take care about the following :
* MLflow, a an open source platform from Databricks that aims to design an open ML platform where organizations can use any ML library and development tool of 
  their choice to reliably build and share ML applications. 
* Open source: MLflow as an open source project that users and library developers can extend. In addition, MLflow’s open format makes it very easy to share 
  workflow steps and models across organizations if you wish to open source your code.MLflow is designed to work with any ML library, algorithm, deployment tool or 
  language.
* MLFlow has following components:
  * MLflow Tracking : An API to log parameters, code, and results in machine learning experiments and compare them using an interactive UI.
  * MLflow Projects : Packaging ML code in a reusable, reproducible form in order to share with other data scientists or transfer to production.
  * MLflow Models:  A model packaging format and tools that let you easily deploy the same model (from any ML library) to batch and real-time scoring on platforms 
    such as Docker, Apache Spark, Azure ML and AWS SageMaker.
  * MLflow Model Registry: A centralized model store, set of APIs, and UI, to collaboratively manage the full lifecycle of MLflow Models.
 
  ![image](https://user-images.githubusercontent.com/13011167/97172697-68d15200-17b5-11eb-8f4c-f1586687dbb6.png)

## A. MLFlow TRACKING Server - Experiment Tracking 
### 1. Concept (Logging API, RUNs)
* Over the course of the machine learning life cycle, data scientists test many different models from various libraries with different hyperparameters. Tracking 
  these various results poses an organizational challenge. In brief, storing experiments, results, models, supplementary artifacts, and code creates significant 
  challenges.

* MLflow Tracking is one of the three main components of MLflow. It is a logging API specific for machine learning and agnostic to libraries and environments that 
  do the training. It is organized around the concept of RUNs, which are executions of data science code. Runs are aggregated into experiments where many runs can 
  be a part of a given experiment and an MLflow server can host many experiments.

* MLflow tracking also serves as a model registry so tracked models can easily be stored and, as necessary, deployed into production. Experiments can be tracked 
  using libraries in Python, R, and Java as well as by using the CLI and REST calls. 
  
### 2. Where Runs Are Recorded
* MLFlow tracking server has two component for storage: a backend store and an artifact store.
  * BACKEND STORE: Where MLFLOW Tracking Server stores experiment and run metadata as well as params, metrics and tags for RUNs. MLFLow supports two types of 
    backend stores - file store and database-backed store.
  * ARTIFACT STORE: It is a location suitable for large data ( such as blob, S3 bucket or shared NFS file system) and is where client log their output (for example 
    models)
* MLflow runs can be recorded to local files, to a SQLAlchemy compatible database, or remotely to a tracking server. By default, the MLflow Python API logs runs locally to files in an mlruns directory wherever you ran your program. You can then run mlflow ui to see the logged runs.
* To log runs remotely, set the MLFLOW_TRACKING_URI environment variable to a tracking server’s URI or call mlflow.set_tracking_uri().

### 3. MLFlow Tracking Server
![image](https://user-images.githubusercontent.com/13011167/97169233-bc40a180-17af-11eb-9785-806d70cf4093.png)

### 4.TRAINING ML MODEL WITH MLFLOW
* Each run can record the following information:
  * Parameters: Key-value pairs of input parameters such as the number of trees in a random forest model.
  * Metrics: Evaluation metrics such as RMSE or Area Under the ROC Curve.
  * Artifacts: Arbitrary output files in any format. This can include images, pickled models, and data files.
  * Source: The code that originally ran the experiment.
  * Tags/Notes: Info about a run.
  * Version: git Version.
 
Training the model with the different hyper-parameters and compare the results. 

### 5. Executing - Experiment Tracking.
   #### a.Installing
        * Install MLflow from PyPI via pip install mlflow.
        * MLflow requires conda to be on the PATH for the projects feature.

   #### b.Running a Sample App With the Tracking API
        * The programs in examples use the MLflow Tracking API. For instance, run:
        * python examples/quickstart/mlflow_tracking.py
        * This program will use MLflow Tracking API, which logs tracking data in ./mlruns. This can then be viewed with the Tracking UI.

   #### c.Launching the Tracking UI
        * The MLflow Tracking UI will show runs logged in ./mlruns at http://localhost:5000. Start it with:
        * mlflow ui

   #### d. Running a Project from a URI
        * The mlflow run command lets you run a project packaged with a MLproject file from a local path or a Git URI:
        * mlflow run examples/sklearn_elasticnet_wine -P alpha=0.4
        * mlflow run https://github.com/mlflow/mlflow-example.git -P alpha=0.4
        * See examples/sklearn_elasticnet_wine for a sample project with an MLproject file.

## B. MLFlow PROJECTS - Packaging ML Projects
### 1. Concept 
* Projects have various library dependencies so shipping a machine learning solution involves the environment in which it was built. MLflow allows for this 
  environment to be a CONDA environment or DOCKER container. This means that teams can easily share and publish their code for others to use.
* Machine learning projects become increasingly complex as time goes on. This includes ETL and featurization steps, machine learning models used for pre-
  processing, and finally the model training itself.
* Each component of a machine learning pipeline needs to allow for tracing its lineage. If there's a failure at some point, tracing the full end-to-end lineage of 
  a model allows for easier debugging.
* ML Projects is a specification for how to organize code in a project. The heart of this is an ML project file, a YAML specification for the components of an ML 
  project. This allows for more complex workflows since a project can execute another project, allowing for encapsulation of each stage of a more complex machine 
  learning architecture. This means that teams can collaborate more easily using this architecture.
  
   ![IMAGE](https://user-images.githubusercontent.com/13011167/94451498-190a6580-01cc-11eb-940c-fa44393b1a4d.png)
  
 ### 2. MLFlow Project options - Local or Remote
  ![image](https://user-images.githubusercontent.com/13011167/97164127-adee8780-17a7-11eb-89e8-fe026991a665.png)
 
 ### 3. MLFlow Code Structure
 * MLProject
 * conda.yaml
 * main.py
 * model.py
 
## C. MLFlow MODELS - Packaging 
### 1. Concept 
* Once a model has been trained and bundled with the environment it was trained in. The next step is to package the model so that it can be used by a varity of 
  serving tools.
* Different deployment options available are:
  * Container-based REST Servers : on demand clicks
  * Spark Streaming: iot, telemetry
  * Batch: Batch scoring
  * Managed cloud platforms such as Azure ML and AWS SageMaker.
* Packaging the final model in a platform-agnostic ways offers the most flexibility in deployment options and allows reuse across a number of platforms.

 ### 2. MLFlow Models integrations with ML Frameworks
![image](https://user-images.githubusercontent.com/13011167/97165453-b647c200-17a9-11eb-8ac0-e243bd0313f4.png)

### 3. MLFlow Models Types
* BATCH Inferencing (Scoring)
  * This represent most of the use cases of ML model deployments
  * This normally means running the predictions from a model and serving them somewhere (db, filesystem etc) for later use.
  * For LIVE serving, results are often saved to the database that will serve the saved predication quickly.
  * Other use cases, such as populating emails, they can be stored in less performant data stores such as a blob store.

* REAL time interfacing
  * Generating predications for a small number of records with fast results ( e.g results in millisec)

### PACKAGING TRAINING CODE IN A CONDA ENVIRONMENT Packaging 
* You do this by using MLflow Projects conventions to specify the dependencies and entry points to your code. The sklearn_elasticnet_wine/MLproject file specifies 
  that the project has the dependencies located in a Conda environment file called conda.yaml and has one entry point that takes two parameters: alpha and 
  l1_ratio.
* To run this project, invoke mlflow run examples/sklearn_elasticnet_wine -P alpha=0.42. After running this command, MLflow runs your training code in a new Conda 
  environment with the dependencies specified in conda.yaml.
* If the repository has an MLproject file in the root you can also run a project directly from GitHub. This tutorial is duplicated in the https://github.com/mlflow/mlflow-example repository which you can run with mlflow run https://github.com/mlflow/mlflow-example.git -P alpha=5

### SERVING THE MODEL
* Now that we have packaged the model using the MLproject convention and have identified the best model, it is time to deploy the model using MLflow. An MLflow 
  Model is a standard format for packaging machine learning models that can be used in a variety of downstream tools — for example, real-time serving through a 
  REST API or batch inference on Apache Spark.
* In the example training code, after training the linear regression model, a function in MLflow saved the model as an artifact within the run.
  [mlflow.sklearn.log_model(lr, "model")]

# MLflow: Managing the Machine Learning Lifecycle 

 ![image](https://user-images.githubusercontent.com/13011167/95012471-7b44e980-0656-11eb-9f33-1ab6127e6435.png)

### MLFlow - Supported Integrations
  ![image](https://user-images.githubusercontent.com/13011167/96889260-0d951c00-14a4-11eb-879f-80b91e4e3631.png)
  ![image](https://user-images.githubusercontent.com/13011167/94446051-c2019200-01c5-11eb-8bc1-42446499616f.png)
   ![image](https://user-images.githubusercontent.com/13011167/91650638-a9f00300-ea9f-11ea-8218-e68cb5de129b.png)
### ENVIRONMENT SETUP for MLFLOW:
  * Step-01 : Install Python. Download the appropiate version from [https://www.python.org/downloads/windows/]. Once Downloaded, run the installer.Make sure you select the Install launcher for all users and Add Python 3.7 to PATH checkboxes. Click Install Now. Verify python is installed by typing ["python" on the command prompt].
  * Step-02 : Install virtualnv. Why? Python software packages are installed system-wide by default. Consequently, whenever a single project-specific package is changed, it changes for all your Python projects. You would want to avoid this, and having separate virtual environments for each project is the easiest solution. [pip install virtualenv].
  * Step-03 : Install MLFlow [pip install mlflow] . Install scikit-learn [pip install scikit-learn].
  * Step-04 : Instal conda. [https://conda.io/projects/conda/en/latest/user-guide/install/index.html]
  * Step-05 : Clone (download) the MLflow repository via git clone https://github.com/mlflow/mlflow .
  * Step-06 : cd into the examples directory within your clone of MLflow - we’ll use this working directory for running the tutorial. We avoid running directly from our clone of MLflow as doing so would cause the tutorial to use MLflow from source, rather than your PyPI installation of MLflow. The code is located at examples/sklearn_elasticnet_wine/train.py .
  * Step-07 : You can run the example with default hyperparameters as follows: [python examples/sklearn_elasticnet_wine/train.py]
  * Step-08 : Comparing the Models: Next, use the MLflow UI to compare the models that you have produced. In the same current working directory as the one that contains the mlruns run [mlflow ui] http://localhost:5000

```
      Command Handy for you during setup the environment:
      Install PIP Windows [python -m pip install -U pip]
      Install PIP MAC [pip install -U pip]
      pip install virtualenv
      pip install scikit-learn
      pip install mlflow

      pip install -U scikit-learn scipy matplotlib
      MACOS
      [Installing Python]
      Homebrew Install : /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
      brew install python@3.8
      python -m pip3 install -U pip3
      pip3 install scikit-learn

      [Installing Conda] - [bash ~/miniconda.sh -b -p $HOME/miniconda]
      brew install wget
      wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -O ~/miniconda.sh
      bash ~/miniconda.sh -b -p $HOME/miniconda

```


### Important Links
* https://github.com/mlflow/mlflow
* https://github.com/mlflow/mlflow/blob/master/CONTRIBUTING.rst
* https://github.com/mlflow/mlflow/blob/master/CONTRIBUTING.rst#building-a-distributable-artifact
* https://github.com/SQLShark/MachineLearningFromModelToProduction
* https://medium.com/syncedreview/google-ai-chief-jeff-deans-ml-system-architecture-blueprint-a358e53c68a5
* https://christophergs.com/machine%20learning/2019/03/17/how-to-deploy-machine-learning-models/
* https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/standard-deployment.html
* https://github.com/Ycallaer/mlflowdocker/blob/master/Dockerfile

  * What is MLflow at a high level? MLflow at a high level by MLFOW Creator (Matei Zaharia): https://databricks.com/session/accelerating-the-machine-learning-lifecycle-with-mlflow-1-0
  * What is a good source for the larger context of machine learning tools? Podcast Roaring Elephant : https://roaringelephant.org/2019/06/18/episode-145-alex-zeltov-on-mlops-with-mlflow-kubeflow-and-other-tools-part-1/#more-1958
  * Where can I find the MLflow docs? https://www.mlflow.org/docs/latest/index.html 
  * Getting started with mlFlow : https://towardsdatascience.com/getting-started-with-mlflow-52eff8c09c61
  * Productizing Machine Learning Models: https://blog.sasken.com/productizing-machine-learning-models-an-introduction#:~:text=The%20typical%20machine%20learning%20
  * https://community.cloud.databricks.com/login.html
  ### Data Bricks Setup  
  * https://www.databricks.training/step-by-step/creating-clusters-on-aws/
  
