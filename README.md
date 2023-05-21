# Suicide-Sex-Classifier
[Dataset]([url](https://www.kaggle.com/datasets/russellyates88/suicide-rates-overview-1985-to-2016))

This model was created using logistic regression and aims to predict which sex commits the majority of suicides in a country for a year.
The response variable is equal to 1 if the majority is was male and 0 otherwise.
I relied on the single dataset to create potentially significant features which initially included: 
1. Country
2. Year
3. Population
4. rates/100k of 5-14
5. rates/100k of 15-24
6. rates/100k  of 25-34 
7. rates/100k of 35-54
8. rates/100k of 55-74
9. rates/100k of 75+
10. total gdp 
11. change in total gdp from last year
12. gdp per capita
13. change in gdp per capita from last year
14. ratio of gdp per capita to total gdp
15. change in ratio of gdp per capita to total gdp from last year

I performed two train-test splits using the train_test_split function from _Sklearn_.
In the first split (⅔ for training, ⅓ for testing), after training the model, I recorded the statistically significant covariates, using $\alpha = 0.5$.
I used the testing set to fit a new model and kept the statistically significant covariates.
In the second split (⅘ for training, ⅕ for testing), I trained a model with the union of all the previously signficant covariates and compared mean squared error and R^2 values for training and testing to ensure there’s no overfitting.


The prediction threshold for the logistic probabilities was >= 0.5 for males and < 0.5 for females. However, 11 thresholds from 0.0 to 1.0 were tested in intervals of 0.1 with a corresponding Receiver Operating Curve that was plotted. The area under the ROC curve indicated that the model performed roughly 36.7% better than a random classifier. The initial steepness
of the curve indicates that when the model threshold is high, the true positive rate increases much faster than the false positive rate. In other words, when the model is very certain that the majority of people who commit suicides in a country is male, it is very likely that males indeed comprise the majority of suicides. On the other hand, the model is less capable of making predictions for lower thresholds.
