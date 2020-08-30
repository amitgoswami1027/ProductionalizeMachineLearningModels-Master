# MFFlow - An Open Source Machine Learning Platform
Machine Learning end to end development and deployment is complex and considering non-determinstic nature of the subject it become more important to straterzie appropiately for intergating it to the business and our products. Moving a model to production can be challenging due to the plethora of deployment tools and environments it needs to run in (e.g. REST serving, batch inference, or mobile apps). There is no standard way to move models from any library to any of these tools, creating a new risk with each new deployment.

ML development brings many new complexities beyond the traditional software development lifecycle. Unlike in traditional software development, ML developers want to try multiple algorithms, tools and parameters to get the best results, and they need to track this information to reproduce work. In addition, developers need to use many distinct systems to productionize models. To address these problems, many companies are building custom "ML platforms" that automate this lifecycle, but even these platforms are limited to a few supported algorithms and to each company's internal infrastructure. In this talk, I present MLflow, a new open source project from Databricks that aims to design an open ML platform where organizations can use any ML library and development tool of their choice to reliably build and share ML applications. MLflow introduces simple abstractions to package reproducible projects, track results, and encapsulate models that can be used with many existing tools, accelerating the ML lifecycle for organizations of any size.

MLflow designed to tkare care about the following :
* Open interface: MLflow is designed to work with any ML library, algorithm, deployment tool or language. It’s built around REST APIs and simple data formats (e.g., a model can be   viewed as a lambda function) that can be used from a variety of tools, instead of only providing a small set of built-in functionality. This also makes it easy to add MLflow to 
  your existing ML code so you can benefit from it immediately, and to share code using any ML library that others in your organization can run.
* Open source: We’re releasing MLflow as an open source project that users and library developers can extend. In addition, MLflow’s open format makes it very easy to share 
  workflow steps and models across organizations if you wish to open source your code.
  
  ![image](https://user-images.githubusercontent.com/13011167/91650638-a9f00300-ea9f-11ea-8218-e68cb5de129b.png)
  
  
  
  ### Important Links
  * Getting started with mlFlow : https://towardsdatascience.com/getting-started-with-mlflow-52eff8c09c61
  * Productizing Machine Learning Models: https://blog.sasken.com/productizing-machine-learning-models-an-introduction#:~:text=The%20typical%20machine%20learning%20
