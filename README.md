# Predict Bike Sharing Demand with AutoGluon

## AWS Machine Learning Engineer Nanodegree Project 1

I performed machine learning on historical bike demand data to predict hourly rentals, using AWS SageMaker & AutoGluon. My initial model performed well, but the greatest gains in performance came after feature-engineering, specifically breaking datetime data into years, months, day of the week, and hour of the day. Hyperparameter tuning only modestly improved my model, suggesting that AutoGluon's default settings are sufficient for this use case.
