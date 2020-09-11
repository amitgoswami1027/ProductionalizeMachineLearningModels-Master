# MFFlow - An Open Source Machine Learning Platform
Machine Learning end to end development and deployment is complex and considering non-determinstic nature of the subject it become more important to straterzie appropiately for intergating it to the business and our products. Moving a model to production can be challenging due to the plethora of deployment tools and environments it needs to run in (e.g. REST serving, batch inference, or mobile apps). There is no standard way to move models from any library to any of these tools, creating a new risk with each new deployment.

ML development brings many new complexities beyond the traditional software development lifecycle. Unlike in traditional software development, ML developers want to try multiple algorithms, tools and parameters to get the best results, and they need to track this information to reproduce work. In addition, developers need to use many distinct systems to productionize models. To address these problems, many companies are building custom "ML platforms" that automate this lifecycle, but even these platforms are limited to a few supported algorithms and to each company's internal infrastructure. In this talk, I present MLflow, a new open source project from Databricks that aims to design an open ML platform where organizations can use any ML library and development tool of their choice to reliably build and share ML applications. MLflow introduces simple abstractions to package reproducible projects, track results, and encapsulate models that can be used with many existing tools, accelerating the ML lifecycle for organizations of any size.

MLflow designed to take care about the following :
* Open interface: MLflow is designed to work with any ML library, algorithm, deployment tool or language. It’s built around REST APIs and simple data formats (e.g., a model can be   viewed as a lambda function) that can be used from a variety of tools, instead of only providing a small set of built-in functionality. This also makes it easy to add MLflow to 
  your existing ML code so you can benefit from it immediately, and to share code using any ML library that others in your organization can run.
* Open source: We’re releasing MLflow as an open source project that users and library developers can extend. In addition, MLflow’s open format makes it very easy to share 
  workflow steps and models across organizations if you wish to open source your code.
  
  ![image](https://user-images.githubusercontent.com/13011167/91650638-a9f00300-ea9f-11ea-8218-e68cb5de129b.png)
  
  ## GETTING STARTED WITH MLFLOW 
  
  ### ENVIRONMENT_SETUP for MLFLOW:
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
### TRANING THE ML MODEL WITH MLFLOW

  
  ## Packaging Training Code in a Conda Environment
  You do this by using MLflow Projects conventions to specify the dependencies and entry points to your code. The sklearn_elasticnet_wine/MLproject file specifies that the project has the dependencies located in a Conda environment file called conda.yaml and has one entry point that takes two parameters: alpha and l1_ratio.
  To run this project, invoke mlflow run examples/sklearn_elasticnet_wine -P alpha=0.42. After running this command, MLflow runs your training code in a new Conda environment with the dependencies specified in conda.yaml.

If the repository has an MLproject file in the root you can also run a project directly from GitHub. This tutorial is duplicated in the https://github.com/mlflow/mlflow-example repository which you can run with mlflow run https://github.com/mlflow/mlflow-example.git -P alpha=5

## Serving the model
Now that you have packaged your model using the MLproject convention and have identified the best model, it is time to deploy the model using MLflow Models. An MLflow Model is a standard format for packaging machine learning models that can be used in a variety of downstream tools — for example, real-time serving through a REST API or batch inference on Apache Spark.
In the example training code, after training the linear regression model, a function in MLflow saved the model as an artifact within the run.
[mlflow.sklearn.log_model(lr, "model")]

# MLflow: Managing the Machine Learning Lifecycle 

## Experiment Tracking with MLFlow
Over the course of the machine learning life cycle, data scientists test many different models from various libraries with different hyperparameters. Tracking these various results poses an organizational challenge. In brief, storing experiments, results, models, supplementary artifacts, and code creates significant challenges.

MLflow Tracking is one of the three main components of MLflow. It is a logging API specific for machine learning and agnostic to libraries and environments that do the training. It is organized around the concept of runs, which are executions of data science code. Runs are aggregated into experiments where many runs can be a part of a given experiment and an MLflow server can host many experiments.

Each run can record the following information:

    Parameters: Key-value pairs of input parameters such as the number of trees in a random forest model
    Metrics: Evaluation metrics such as RMSE or Area Under the ROC Curve
    Artifacts: Arbitrary output files in any format. This can include images, pickled models, and data files
    Source: The code that originally ran the experiment

MLflow tracking also serves as a model registry so tracked models can easily be stored and, as necessary, deployed into production.

Experiments can be tracked using libraries in Python, R, and Java as well as by using the CLI and REST calls. This course will use Python, though the majority of MLflow functionality is also exposed in these other APIs.







  
  ### Important Links
  * Getting started with mlFlow : https://towardsdatascience.com/getting-started-with-mlflow-52eff8c09c61
  * Productizing Machine Learning Models: https://blog.sasken.com/productizing-machine-learning-models-an-introduction#:~:text=The%20typical%20machine%20learning%20
