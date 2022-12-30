# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Archana Pradeep

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I realised I needed to set all the values in my predictions to be non-negative or else Kaggle wouldnt accept them.

```
predictions[predictions<0].count()
```

### What was the top ranked model that performed?
It was WeightedEnsemble_L3 at first but after the new features were introduced and the hyperparameter tuning was in place, it was WeightedEnsemble_L2.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
* I realised that there were a couple of columns which had discrete values so they could be categorised like Season and Weather. 
* I also noticed the datetime column wasn't being used at all so I made features out of it - Day, Month, Year and Hour.


### How much better did your model preform after adding additional features and why do you think that is?
The first model had a public kaggle score of 1.38533 while the second model with the additional features had a public kaggle score of 0.55702. Thats an almost 60% decrease in the scores caused due to the correct categorisation of season and weather and also through the introduction of new features I leveraged from the datetime column

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Surprisingly there was not much of a difference between trying different hyper parameters, this is perhaps because I only tried a preset number of models which didn't quite work with the data

### If you were given more time with this dataset, where do you think you would spend more time?
Hyperparameter tuning, to see if I can make more improvement on the score 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|best_quality|600|none|1.38533|
|add_features|best_quality|600|none|0.55702|
|hpo|best_quality|600|{"RF,XGB, NN, CAT, GBM, XT"}|0.55230|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.


![model_test_score.png](img/model_test_score.png)

## Summary
As illustrated in the diagram there was a sharp increase in performance with the exploratory data analysis phase of this exercise, however the performance plateaus even as I attempted to perform hyperparameter tuning. Given more time, This is what I would focus on.
