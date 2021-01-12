




PROBLEM DEFINITION

We are familiar with the roadmap for solving a data science problem. It requires manual intervention to cover each phase of the data science workflow. It takes up a lot of time to analyze each feature manually.

OBJECTIVE

There are no generic approaches to solve any kind of machine learning problem, where the system automatically communicates with every phase of the data science workflow. The project aims to cover end-to-end automation of the complete data science workflow for every problem definition.

PHASE 1

There are certain phases that make the ground for data science. These phases need to communicate automatically to each other. The input of each phase is the output of its predecessor. In the end, the output will be a model that has got the best score in all of the models, along with it a python file would be there, named 'DataScience_Lifecycle.py' which has tracked the feature engineering done for the given dataset.So that we could recreate this scenario at any time.

PHASE 2

We can make use of machine learning models like regression, classification, clustering to identify more features, to get much better insights while doing feature engineering.

WORKFLOW

The system accepts three parameters as its input and they are file location, the target variable, and the type of problem i.e Regression, Classification, and Clustering. In the case of clustering, we pass the target variable as None. Then the system would do a generalistic exploratory data analyzes and feature engineering for each feature that the dataset has.

Replace nan values with the most frequent value of the feature.

 If a feature matches the regex of time, the hour is extracted from that particular feature, then for a DateTime feature, features like a weekday, year, month, age, hour are extracted. 

It is possible to get Country, City, latitude, longitude of an IP address using the pygeoip module if any features match with the regex of an IP. “pyGeoIP” module can be used to map or correlate IP addresses with the physical location. It can be done by downloading a free database called GeoLiteCity.dat. So for an IP address, it is possible to get the country name, city, latitude, longitude, postal code, etc.

Username and domain name are extracted from a feature like email-id.

Protocol, sub-domain, domain, top-level domain are taken from a feature like URL. 


 

Then the system checks for a total null value percentage for every feature. It drops features that have got a null value percentage greater than 99. 

Then the control will move to categorical encoding. Features with object data type are selected. 

If any feature is identified to be a text, TF-IDF vectorization is done for those features. If the total number of unique values is less than 20%, perform one-hot encoding for those categorical features else perform frequency encoding. If the target variable is categorical, perform label encoding.

 Then the dataset is made standardized and PCA is done for feature selection.

Then the system checks the type of problem that has been passed into it. If it is a regression problem, a data frame is created with the names of the different regression models as its indices and their hyperparameters are taken to be its columns.

 Using Grid Search, fine-tune every model hyperparameters for model optimization. The best hyperparameters of every model get stored in the data frame. Then each model gets trained with the dataset using its respective best hyperparameters.

 The best regression model will be the model that has got the least rmse and along with comparing the time taken for execution. 

For a classification problem, just like regression, a data frame is created with different classification model's names as its indices and their hyperparameters are taken to be its columns. Then start optimizing the hyperparameters. 

The model that has got the highest accuracy along with comparing the time taken for execution is taken as the best classification model. 

For clustering, the model which has got the largest silhouette_score is taken as the best model.

Saved the finalized model as a pickle file for future usage. 

