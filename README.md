# The-MLC-Projects: Classification of Benign or Malware Android Apps


## Task
Classify whether an android app is benign or malware.


## Exploratory Data Analysis
The data set called Android App Permission Dataset had 184 columns consisting of the features, name of the app, app descrption and the category of the app. The target feature had binary varibles that classified whether an app was benign or not.

5 columns with were removed from the data as it doesn't influence the outcome of the target column. These columns were:  names of Apps, Related Apps, Description and Package.

22 columns with zero values in each row were dropped from the data.

204 rows were removed from the data that had missing values.

The resulting dataset had 157 columns including the target column left in the data. A further preprocessing step of feature selection to find the features that are highly correlated with the target feature was done as 157 columns is computationally expensive to run a model.

A feature selection step was done using XGBoost and 36 features were selected that were highly correlated with the target feature.


## Model Selection and Analysis
An analysis was done on the models using Logistic regression, KNN Classifier, Decision Tree, Random Forest, XGBoost and LightGM. The random forest classifier had the best model accuracy of 73.5% and on further hyperparameter tuning, the model's accuracy improved to 74.1%


## Model Explainability
The top 3 features that greatly influences the outcome of an Android app are: 

- Number of ratings

- Price

- Rating

The SHAP dependence plots shows how the selected features interact with the target variable and it also shows which other feature it interacts with mostly. From the selected top 3 features, the dangerous permission count interacts with 2 of the top 3 showing it's an important feature to monitor.

Rating is the only feature that shows a linear relationship with the target feature.

On the 8th observation, the feature 'communication: view network state' pushed the model to score high whereas the features 'price and number of ratings' pushed the score of the model slighly lower.

On the 100th observation, the feature 'price' pushed the model to score high wheareas the features 'number of ratings, network communication, view WIFI state, network communication, view network state and dangerous permission counts pushed the model score lower.

At the 815th observation, there are more features than one that are pushing the model to have a high score.

This shows that the final selected features each have an impact in the model thus none should be removed.



# The-MLC-Projects: Prediction of trip time


## Task
To predict the trip-time precisely for the advancement of Intelligent Transport Systems (ITS) and traveller information systems. 


## Exploratory Data Analysis
The data set had 26 columns and 9,601,139 rows. The first row was removed as it's a copy of the index column. The resulting dataset had 25 columns and no null values.

The scatter plot analysis between the target features (Duration) and the other features:

- The target feature is strongly correlated to distance and haversine distance.

- The target feature is weakly correlated to pick up hour, drop off hour, temperature and ground tempature.

- The target feature has no very little correlation with the rest of the features: PLong, PLatd, DLong, DLatd, Pmonth, PDay, Pmin, Dmonth, Dday, Dmin, wind, humid, solar, PDweek, DDweek, Precipitation, snow and dust.

- From the above, the features that are most applicable for modeling are distance, haversine distance, pick up hour, drop off hour, temperature and ground temparature.

The data set was scaled using the MinMax Scaler so that all values ranged between 0 and 1.


## Model Selection and Analysis
An analysis was done on the best regression models to use using Linear regression, Ridge Regression, Decision Tree, XGBoost and LightGBM. 

The light GBM has a good performance with an R squared of 81.7% meaning 81.7% of the data fits into the regression model. It has a mean absolute error of 0.05 which means that the actual duration time will miss the predicted time by 0.05. The Mean squared error is also quite low giving us more confidence in the choice of this model.


## Model Explainability
The features that contribute to the trip duration of a bicycle are:

- Distance
- Harvesine distance (great-circle distance between two points on a sphere)
- Pick up hour of the bicycles
- Drop off hour of the bicycles
- Temperature
- Ground temperature

From the summary plot, we can see that the lower distances reduced the trip duration. So did lower temperatures, lower harvesine distances and low drop off hours. High pick up hours reduced the trip duration.

The dependence plots shows how the selected features interact with the target variable and it also shows which other feature it interacts with mostly. The drop off hour interacts with the pickup hour while the distance interacts with harvesine distance. The tempereture interacts with the distance too.

At the first observation, the harvesine distance pushed the score of the model high while the drop off hour, pick up hour and distance pushed the model to score low.

At the 105th observation, the harvesine distance pushed the model to score low wheareas temperature, ground temperature, distance and pickup hour pushed the model score higher. The temperature did not affect the score of the model at this observation.

Each feature has an impact on the model at each observation.


