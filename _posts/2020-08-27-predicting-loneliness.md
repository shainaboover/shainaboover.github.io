---
layout: post
title: Predicting Loneliness
subtitle: Can we predict who is lonely based on hobbies, fears, and opinions?
cover-img: https://github.com/shainaboover/Loneliness/blob/master/lonely_3.jpg?raw=true
# tags: [books, test]
---

I chose a dataset that surveyed a little over 1000 young people on their hobbies, fears, and personal opinions.
I wanted to see whether I could predict loneliness based on these factors. 

The data was fairly easy to work with as most values were on a scale of 1-5, with 5 representing 'highly agree' with survey question.
For an explanation of the survey questions, you can refer to the [<span style="font-size:12pt;">description</span>](https://www.kaggle.com/miroslavsabo/young-people-survey?select=columns.csv) on Kaggle.

I was only interested in those who reported severe feelings of loneliness, so I made the target class binary with 1 representing severe loneliness (those who answered a 4 or 5) and 0 representing all others (average to low levels of loneliness). This resulted in imbalanced classes and I chose precision as my metric. I wanted to see how often the models were able to predict severe loneliness.

First, I maded a some simple models and found which features were most correlated with loneliness. I chose to use the top 20 features from a random forest model. Intuitively, I can see how many of these features would relate to loneliness in others as well as my own life.
![alt text](https://github.com/shainaboover/Loneliness/blob/master/feature_importances.png?raw=true)

Next I fit a few models (including logistic regression, decision tree, random forest, xgb) and compared which ones were performing best. My Random Forest and Gradient Boosting models out performed the others but gave me very similar metrics. 

I found that the two models had pretty big differences in how they prioritized the variables. Here is what each model, Random Forest and XGB respectively, ranked the features.

![alt text](https://github.com/shainaboover/Loneliness/blob/master/rf_permutation_importances.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xbg_permutation_importances.png?raw=true)

Despite those differences, they produced very similar confusion matrices. Both were able to predict severe loneliness with a relatively high level of precision, still they tended to wrongly predict that someone was lonely when they were not. Again Random Forest and XGB, respectively. 

![alt text](https://github.com/shainaboover/Loneliness/blob/master/rf_confusion_matrix.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xgb_confusion_matrix.png?raw=true)

I also found very similar, albeit, not great ROC curves

![alt text](https://github.com/shainaboover/Loneliness/blob/master/rf_roc_curve.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xgb_roc_curve.png?raw=true)

When the models were run on my validation set, the precision metric was pretty high!
![alt text](https://github.com/shainaboover/Loneliness/blob/master/metrics_validation.png?raw=true)

But when run on the test set, the accuracy droped to baseline level

![alt text](https://github.com/shainaboover/Loneliness/blob/master/random_forest_report.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xgb_report.png?raw=true)

