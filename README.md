# Productization of Machine Learning Models Using MLFLOW
ML is required in exactly those cases when the desired behavior cannot be effectively expressed in software logic without dependency on external data.

How to integrate the machine learning models to production ready code. !!

Deployment of machine learning models, or simply, putting models into production, means making your models available to your other business systems. By deploying models, other systems can send data to them and get their predictions, which are in turn populated back into the company systems. Through machine learning model deployment, you and your business can begin to take full advantage of the model you built.

When we think about data science, we think about how to build machine learning models, we think about which algorithm will be more predictive, how to engineer our features and which variables to use to make the models more accurate. However, how we are going to actually use those models is often neglected. And yet this is the most important step in the machine learning pipeline. Only when a model is fully integrated with the business systems, we can extract real value from its predictions.

### Machine Learning Reproduciability Crisis
It’s hard to explain to people who haven’t worked with machine learning, but we’re still back in the dark ages when it comes to tracking changes and rebuilding models from scratch. It’s so bad it sometimes feels like stepping back in time to when we coded without source control.
To explain why, here’s a typical life cycle of a machine learning model:
* A researcher decides to try a new image classification architecture.
* She copies and pastes some code from a previous project to handle the input of the dataset she’s using.
* This dataset lives in one of her folders on the network. It’s probably one of the ImageNet downloads, but it isn’t clear which one. At some point, someone may have removed some of the images that aren’t actually JPEGs, or made other minor modifications, but there’s no history of that.
* She tries out a lot of slightly different ideas, fixing bugs and tweaking the algorithms. These changes are happening on her local machine, and she may just do a mass file copy of the source code to her GPU cluster when she wants to kick off a full training run.
* She executes a lot of different training runs, often changing the code on her local machine while jobs are in progress, since they take days or weeks to complete.
* There might be a bug towards the end of the run on a large cluster that means she modifies the code in one file and copies that to all the machines, before resuming the job.
* She may take the partially-trained weights from one run, and use them as the starting point for a new run with different code.
* She keeps around the model weights and evaluation scores for all her runs, and picks which weights to release as the final model once she’s out of time to run more experiments. These weights can be from any of the runs, and may have been produced by very different code than what she currently has on her development machine.
* She probably checks in her final code to source control, but in a personal folder.
* She publishes her results, with code and the trained weights.
* Blog for details: [ https://petewarden.com/2018/03/19/the-machine-learning-reproducibility-crisis/ ]

## Machine Learning Model Deployment
### Machine Learning Pipeline
* DATA Gathering. 
* DATA Analysis : What variables we can use and what variables we cannot use.
* DATA PRE-PROCESSING: During feature engineering, we transform the variable to make them useful in the machine learning models, filling missing values etc.
* FEATURE Selection: Why we need to select feature in first place? Feature selections means finding those variables which are most predictive one and building the models around those variables.
* MODEL BUILDING: Typically build various ML algos and choose the ones which give the best results. 
* UPLIFT IN Business Value: Model bring the actual business value.
* MODEL DEPLOYMENT

![image](https://user-images.githubusercontent.com/13011167/92307830-c071ef00-efb6-11ea-98d8-ce107a957ff0.png)

### Machine Learning Pipeline : Feature Engineerng
* Missing Data: Missing values within the data.
* Labels: Stings in the caterogical Variables. Values of the variables are string rather then numbers, we cannot use it in scikit libraries.
* Distribution of Variables: Gauession Distribution or skewed.
* Outliers.

### Machine Learning Pipeline : Feature Selection
* Allows to find best subset of feature which will allows most predictive features. 
* Simple models are easier to predict and esier to train.
* Enhance generalization by reducing overfitting.
* Utilizing the less number of features reduces the risk of data errors in the models. Data is redundent means many features provide the same informaiton then why should we use more number of the features.
* Less variables we use, we need to write less code for engineering the models and productizing it.
* Embedded Methods, Wrapper methods and filter methods. Filter methods (simple staticical test) - this methods are build on the basis of the feature characteristics. It look into one feature at the time so not take care of overall redundancy. Wrapper methods evaluate all the possible feature comninations for the particular algorithms. Embedded method have flavor of both. 

### Machine Learning Pipeline : Model Building
* Buidling Machine Learning models - Linear models, decision trees models or clustering models.
* Evaluate the preformance about how the model is behaving. Eg: RSE, RMSE etc.
* Meta Ensembling

## Machine Learning Model Building Pipeline : Data Analysis
* Deploying the models does not just means, deploying the machine learning algorithms but we rather need to deploy the entire pipeline. 

# MACHINE LEARNING SYSTEM ARCHITECTURE
* Machine Learning in production required different componenets - Infrastructure, Applications, Data, Documentation and configrations.
* Architecture is how these system intracts with each other to form a system.
* Developing & deploying ML systemsis relatively fast and cheap but maintaining them effectively over a preiod of time is difficult. Clarity in planning and architecture design is very important. ML system require close co-operations between data science, engineering, devops and business, so and shared understanding of the system helps in better co-operation.

### Challanges and Key Principles of the ML Systems
* Need for Reproduciability (Versioning Softwares).
* Entanglement. (Changing anything changing everything principle)
* Data Dependencies. (Most consequensial difference between traditional webapp and ML pipeline is the fact that primary inputs to the systems are not just code, while there are two equal consequensial inbound components i.e code+data. )
* Configration issues. 
* Data and feature Engineering.
* Models errors are hard to detect with traditonal tests.
* Separation of expertise.

![image](https://user-images.githubusercontent.com/13011167/92318504-f2bd3400-f02a-11ea-9812-9c6fe1ace649.png)

### Principles of ML System Architecture
* Reproduciability : Have the ability to replicate the given ML prediction.
* Automation: Retain, update and deploy models as a part of automation pileline.
* Extensibility: Have the ability to easily add and update the models.
* Modulairty: Preprocessing feature engineering code used in training should be organized in the clear pipelines.
* Scability: Ability to serve model predictions to large number of customers.
* Testing: Test variations between models.

### DESIGN APPROACH TO ML SYSTEM ARCHITECTURE 
* Train by batch, predict on fly and Serve Via REST API. (e.g Model train and presisted offline and loaded into webapp that give real time prediction about the price of the house when details about the given house is posted by client using the rest APIs.)
* Train by batch, predict by batch and serve via database. (User might upload the CSV of the house with the input details and wait for 30 min telling them to check the email for details/results. This app will do the batch queue and will be stored in db for web app to share the results.)
* Train and predict by streaming. (App would have access to the conver belt of updated data and models, it would be combination of the streaming framework such as spark stream with the data and updates models been feed from dedicated distributed queue such as apache kafka or aws kenisis. )
* Train by batch and predict by mobile (on the client) : IOS App using the core ML Framework will not need to call the core backend framework for prediction, instead prediction will be made on the device. 

![image](https://user-images.githubusercontent.com/13011167/91441372-b7ce3a00-e88d-11ea-84b5-3b5092c52c76.png)

### Why is Reproduciability in ML Architecture???
Reproducibility is the ability to duplicate the ML Model exactly, such that the same raw data as input, both return the same result. We don't generally deploy ML algorithms but we deploy the entire ML pipeline. We need to make sure that every single step of the ML pipeline is reproduciable. Every Steps in ML Pipeline should be reproduciable.
#### Reproducibility Data gathering
* Problem : Data can be most difficult challange in the reproducibility.  e.g Databases can be constantly updated and overwritten, so values present at certain point may differ. Order of data during data loading is different,eg while retrieving the rows from SQL. 
* Solution : Save the snapshot of the training data, either actual data or reference to it in the AWS.
Desing the data source with the timestramps, so data at any point in time can be retrieved. (Ideal Solution)
#### Reproducibility during Feature Creation
* Problem: Replacing missing data with random values.Replacing the lables with the percentage of the data.Calculating the average values for replacing the missing values.
* Solutions: Apply some coding best practices. Maintan in the version control and publish with auto-incremented or timestramp hashed versions.
#### Reproducibility during Model building
* Record the order with which you pass features to the model, For the models require randomness (decision tree, neural network) need to use the SEEDS. 
#### Reproducibility during Model Deployment
* Software version should match exactly.
* Use container for trackng the verisons.
* Research & deployment should be done in the same language. 


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

### Basic Comcepts 
* MLflow is an MLOps tool that can be used to increase the efficiency of machine learning experimentation and productionalization.
* MLflow lets you train, reuse, and deploy models with any library and package them into reproducible steps that other data scientists can use as a “black box”, 
  without even having to know which library you are using.


### MLflow designed to take care about the following :
* MLflow, a an open source platform from Databricks that aims to design an open ML platform where organizations can use any ML library and development tool of 
  their choice to reliably build and share ML applications. 
* Open source: MLflow as an open source project that users and library developers can extend. In addition, MLflow’s open format makes it very easy to share 
  workflow steps and models across organizations if you wish to open source your code. MLflow is designed to work with any ML library, algorithm, deployment tool 
  or language.
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

# How to setup MLflow in Local
## MlFlow Tracking Server Setup
* Tracking server is user interface and metastore of MLFlow. All the RUNs of ML Experiments can be tracked using the MLFlow Tracking UI.

### Environment Setup
 Create a new conda environment for hosting the MLFlow. 
 
 ```
 conda create -n mlflow_env 
 conda activate mlflow_env
 
 ```
 Then we have to install the MLflow library:
 
 ```
 conda install python 
 pip install mlflow
 ```
Run the following command to check that the installation was successful:

```
mlflow --help
```

By default, the MLflow Python API logs runs locally to files in an mlruns directory wherever you ran your program. You can then run mlflow ui to see the logged runs.

### RUN
We train the linear regression model that takes two hyperparameters: alpha and l1_ratio.
* The MLflow Tracking APIs log information about each training run like hyperparameters (alpha and l1_ratio) used to train the model, and metrics (root mean square 
  error, mean absolute error, and r2) used to evaluate the model. The example also serializes the model in a format that MLflow knows how to deploy.
* Each time you run the example MLflow logs information about your experiment runs in the directory mlruns.
* python train.py <alpha> <l1_ratio>
* mlflow ui
* By default --backend-store-uri is set to the local ./mlruns directory (the same as when running mlflow run locally), but when running a server, make sure that 
  this points to a persistent (that is, non-ephemeral) file system location.

```
mlflow server --default-artifact-root file:/home/your_user/mlruns -h 0.0.0.0 -p 8000
```
Now the Tracking server should be available a the following URL: http://0.0.0.0:8000. However, if you Ctrl-C or exit the terminal, the server will go down. 

* In order to start tracking everything under this Tracking Server it is necessary to set the following environmental variable on .bashrc:
```
export MLFLOW_TRACKING_URI='http://0.0.0.0:8000'
. ~/.bashrc
```

### Example
* We can easily run existing projects with the mlflow run command, which runs a project from either a local directory or a GitHub URI:
* By default mlflow run installs all dependencies using conda.

```
mlflow run sklearn_elasticnet_wine -P alpha=0.5
mlflow run https://github.com/mlflow/mlflow-example.git -P alpha=5.0

local test → mlflow run . -P <param>
github test →mlflow run git://<project-url> <param>
```

* This run will generate a new entry in your tracking server http://0.0.0.0:8000 alongside with a new folder in which the model and the configuration is stored 
(~/mlruns/0/some_uuid). Let’s check it:

```
ls -al ~/mlruns/0
```

* Get the uuid related to the execution from the previous output and substitute the string “your_model_id”

```
mlflow models serve -m ~/mlruns/0/your_model_id/artifacts/model -h 0.0.0.0 -p 8001
```

* What you have just done is serving your model as an HTTP endpoint in your server IP and port 8001 (be careful not having any service listening there), so that it is ready for receiving incoming data to return predictions. You can then query your model with a simple curl command

```
curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["alcohol", "chlorides", "citric acid", "density", "fixed acidity", "free sulfur dioxide", "pH", "residual sugar", "sulphates", "total sulfur dioxide", "volatile acidity"],"data":[[12.8, 0.029, 0.48, 0.98, 6.2, 29, 3.33, 1.2, 0.39, 75, 0.66]]}' http://0.0.0.0:8001/invocations
```


## Important Links-01
* https://ml-ops.org/content/mlops-principles
* https://developer.ibm.com/technologies/data-science/articles/first-impressions-mlflow/
* https://towardsdatascience.com/complete-data-science-project-template-with-mlflow-for-non-dummies-d082165559eb
* https://github.com/mlflow/mlflow
* https://github.com/mlflow/mlflow/blob/master/CONTRIBUTING.rst
* https://github.com/Ycallaer/mlflowdocker/blob/master/Dockerfile
* https://analyticsweek.com/content/using-mlops-with-mlflow-and-azure/
* https://www.logicalclocks.com/blog/mlops-with-a-feature-store
* https://www.mosaicdatascience.com/2020/10/16/mlflow-mlops-tipsand-tricks-blog/
* [Production] https://pedro-munoz.tech/how-to-setup-mlflow-in-production/
* Getting started with mlFlow : https://towardsdatascience.com/getting-started-with-mlflow-52eff8c09c61
* What is MLflow at a high level? MLflow at a high level by MLFOW Creator (Matei Zaharia): https://databricks.com/session/accelerating-the-machine-learning-lifecycle-with-mlflow-1-0
* https://www.databricks.training/step-by-step/creating-clusters-on-aws/
* MLFLOW on AWS : https://allcloud.io/blog/organise-your-ml-experiments-with-mlflow-on-aws/
* [MLOPS-1] https://cloud.google.com/solutions/machine-learning/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning
* [MLOPS-2] https://d1.awsstatic.com/whitepapers/mlops-continuous-delivery-machine-learning-on-aws.pdf?did=wp_card&trk=wp_card
  

## Important Links-02
* [MartinFowler] https://martinfowler.com/articles/cd4ml.html#ml-pipeline-1.png
* [MartinFowler] https://martinfowler.com/articles/data-monolith-to-mesh.html
* [How to Deploy Machine Learning Models] https://christophergs.com/machine%20learning/2019/03/17/how-to-deploy-machine-learning-models/
* [Shadow Mode]https://christophergs.com/machine%20learning/2019/03/30/deploying-machine-learning-applications-in-shadow-mode/
* [Rendezvous Architecture for Data Science in Production-01] https://towardsdatascience.com/rendezvous-architecture-for-data-science-in-production-79c4d48f12b
* [Rendezvous Architecture for Data Science in Production- AWS] https://www.bigdatarepublic.nl/articles/machine-learning-models-aws-rendezvous-architecture/
* [Rrendezvous Architecture Code] https://github.com/ddotabma/rendezvous-on-aws
* [AWS Deployments - Blue/green/Canery etc] https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/standard-deployment.html
* [Talk on ML Deployment] https://www.youtube.com/watch?v=7jKTofl2vmM
* [Surprising Complexity of Randomness] https://www.kdnuggets.com/2017/06/surprising-complexity-randomness.html
* [Azure ML MachineLearning From Model To Production] https://github.com/SQLShark/MachineLearningFromModelToProduction
* [Build and DeployM ML with Apache Kafka] https://www.confluent.io/blog/build-deploy-scalable-machine-learning-production-apache-kafka/
* [Apache Kafka to Drive Machine Learning] https://www.confluent.io/blog/using-apache-kafka-drive-cutting-edge-machine-learning/
* [Streaming Kafka Example] https://github.com/kaiwaehner/kafka-streams-machine-learning-examples
* [Machine Learning Basic & Details - Imp] https://www.ritchieng.com/machine-learning-systems-design/
* [Best MLflow Alternatives] https://neptune.ai/blog/the-best-mlflow-alternatives
* [Tools] https://tox.readthedocs.io/en/latest/config.html#cmdoption-tox-r ; https://docs.pytest.org/en/latest/
* [Deep Learning with Apache Spark] https://towardsdatascience.com/deep-learning-with-apache-spark-part-1-6d397c16abd
* BUILDING VS BUY : https://algorithmia.com/blog/machine-learning-framework
