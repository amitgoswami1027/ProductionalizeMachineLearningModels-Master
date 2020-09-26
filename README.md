# Productization of Machine Learning Models
How to integrate the machine learning models to production ready code. !!

Deployment of machine learning models, or simply, putting models into production, means making your models available to your other business systems. By deploying models, other systems can send data to them and get their predictions, which are in turn populated back into the company systems. Through machine learning model deployment, you and your business can begin to take full advantage of the model you built.

When we think about data science, we think about how to build machine learning models, we think about which algorithm will be more predictive, how to engineer our features and which variables to use to make the models more accurate. However, how we are going to actually use those models is often neglected. And yet this is the most important step in the machine learning pipeline. Only when a model is fully integrated with the business systems, we can extract real value from its predictions.

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

## PYTHON ENVIRONMENT SETUP ON MAC
### Install Python : 


## TRAIN BY BATCH and PREDICT ON FLY (STEPS TO AUTOMATE THE CI/CD ML PIPELINE)








Meta Ensembling

![image](https://user-images.githubusercontent.com/13011167/91420412-4df46700-e872-11ea-8501-0598139e72d8.png)


Setup
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
https://pip.pypa.io/en/stable/installing/

MYBlog Material
https://petewarden.com/2018/03/19/the-machine-learning-reproducibility-crisis/
https://www.confluent.io/blog/build-deploy-scalable-machine-learning-production-apache-kafka/
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


## Important Links
* https://towardsdatascience.com/rendezvous-architecture-for-data-science-in-production-79c4d48f12b
* Randomness: https://www.kdnuggets.com/2017/06/surprising-complexity-randomness.html
* Embrace Randomness in Machine Learning : https://machinelearningmastery.com/randomness-in-machine-learning/
* Apache Kafka to Drive Machine Learning https://www.confluent.io/blog/using-apache-kafka-drive-cutting-edge-machine-learning/
* Streaming Examples : https://github.com/kaiwaehner/kafka-streams-machine-learning-examples
* Deep Learning Spark: https://towardsdatascience.com/deep-learning-with-apache-spark-part-1-6d397c16abd
* MLFLOW : https://github.com/mlflow/mlflow
* https://github.com/ddotabma/rendezvous-on-aws
* https://github.com/SQLShark/MachineLearningFromModelToProduction
* https://medium.com/syncedreview/google-ai-chief-jeff-deans-ml-system-architecture-blueprint-a358e53c68a5
* https://christophergs.com/machine%20learning/2019/03/17/how-to-deploy-machine-learning-models/
* RENDEZVOUS ARCHITECTURE:https://www.bigdatarepublic.nl/articles/machine-learning-models-aws-rendezvous-architecture/
* https://neptune.ai/blog/the-best-mlflow-alternatives

