# Productization of Machine Learning Models
How to integrate the machine learning models to production ready code. !!

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




## Important Links
* https://towardsdatascience.com/rendezvous-architecture-for-data-science-in-production-79c4d48f12b
