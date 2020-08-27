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
![image](https://user-images.githubusercontent.com/13011167/91420412-4df46700-e872-11ea-8501-0598139e72d8.png)

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

![image](https://user-images.githubusercontent.com/13011167/91439799-3d9cb600-e88b-11ea-994e-b181962c2913.png)

### DESIGN APPROACH TO ML SYSTEM ARCHITECTURE 
* Train by batch, predict on fly and Serve Via REST API. (e.g Model train and presisted offline and loaded into webapp that give real time prediction about the price of the house when details about the given house is posted by client using the rest APIs. )
* Train by batch, predict by batch and serve via database. (User might upload the CSV of the house with the input details and wait for 30 min telling them to check the email for details/results. This app will do the batch queue and will be stored in db for web app to share the results.)
* Train and predict by streaming. (App would have access to the conver belt of updated data and models, it would be combination of the streaming framework such as spark stream with the data and updates models been feed from dedicated distributed queue such as apache kafka or aws kenisis. )
* Train by batch and predict by mobile (on the client)

![image](https://user-images.githubusercontent.com/13011167/91441372-b7ce3a00-e88d-11ea-84b5-3b5092c52c76.png)

![image](https://user-images.githubusercontent.com/13011167/91442017-d6810080-e88e-11ea-93d0-207064056f78.png)







## Important Links
* https://towardsdatascience.com/rendezvous-architecture-for-data-science-in-production-79c4d48f12b
* Randomness: https://www.kdnuggets.com/2017/06/surprising-complexity-randomness.html
* Embrace Randomness in Machine Learning : https://machinelearningmastery.com/randomness-in-machine-learning/
* Apache Kafka to Drive Machine Learning https://www.confluent.io/blog/using-apache-kafka-drive-cutting-edge-machine-learning/
* Streaming Examples : https://github.com/kaiwaehner/kafka-streams-machine-learning-examples
* Deep Learning Spark: https://towardsdatascience.com/deep-learning-with-apache-spark-part-1-6d397c16abd
