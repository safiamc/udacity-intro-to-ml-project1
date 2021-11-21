# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Safia CHETTIH

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The competition asks us to predict the total number of bikes rented during hour-long periods on the 20th day of the month, based on hourly data from the first 19 days of the month. My initial model sometimes predicted negative bike rental, which is physically impossible. Therefore I had to change all negative predictions to 0 before submitting my predictions.

### What was the top ranked model that performed?
The top-ranked model was a Weighted Ensemble L3.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The EDA showed that some of the features, such as 'weather' and 'holiday', were qualitative and should be treated as categorical variables. Additionally, the 'datetime' feature would give us much more predictive power when broken down into year, month, day, etc, since it is reasonable to assume that the data is roughly cyclical. For example, we can predict that any given Tuesday will roughly resemble all the other Tuesdays present in the data set. Therefore I created 5 additional features out of 'datetime': year, month, day, day of the week, hour.

### How much better did your model preform after adding additional features and why do you think that is?
This model performed significantly better! The Kaggle score dropped from approximately the 94th percentile to the 27th percentile (based on the now-closed Leaderboard). I think my intuition was correct, that the data has some cyclical patterns with respect to the hour of the day, day of the week, month of the year, etc, which vastly improve the predictive accuracy of the model.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Hyperparameter tuning did not improve the performance of my model on the test data. The Kaggle score decreased slightly, from 0.45651 to 0.46976. I tried increasing the time limit on the AutoGluon algorithm, but that did not increase my Kaggle score.

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time on feature engineering, for example looking into the feature importance and removing features from the training dataset that have low correlations to count. Additionally, code posted on Kaggle from some of the very-low-score submissions suggest that 'count' is right-skewed, so I could use a transformation on my predictions to take that into account.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hyperparameter_tune_kwargs|time_limit|score|
|--|--|--|--|
|initial|None|600|1.39584|
|add_features|None|600|0.45651|
|hpo_v1|'auto'|600|0.46976|
|hpo_v2|'random'|600|0.46976|
|hpo_v3|'random'|1000|0.46976|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary

