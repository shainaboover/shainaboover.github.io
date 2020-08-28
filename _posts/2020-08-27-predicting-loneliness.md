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
For an explanation of the survey questions, you can refer to the [<span style="font-size:12pt;">description</span>](https://www.kaggle.com/miroslavsabo/young-people-survey?select=columns.csv) on Kaggle. The sections I chose were: HOBBIES & INTERESTS, PHOBIAS, and PERSONALITY TRAITS, VIEWS ON LIFE & OPINIONS.

I was only interested in those who reported severe feelings of loneliness, so I made the target class binary with 1 representing severe loneliness (those who answered a 4 or 5) and 0 representing all others (average to low levels of loneliness). This resulted in imbalanced classes (0 at 74% and 1 at 26%) and I chose precision as my metric. I wanted to see how often the models were able to predict severe loneliness.

First, I made some simple models and found which features were most correlated with loneliness. I chose to use the top 20 features from a random forest model. Intuitively, I can see how many of these features would relate to loneliness in others as well as my own life.
![alt text](https://github.com/shainaboover/Loneliness/blob/master/feature_importances.png?raw=true)

Next I fit a few models (including logistic regression, decision tree, random forest, xgb) and compared which ones were performing best. My Random Forest and Gradient Boosting models out performed the others but gave me very similar metrics. 

I found that the two models had pretty big differences in how they prioritized the variables. Here is how each model, Random Forest and XGB respectively, ranked the features.

![alt text](https://github.com/shainaboover/Loneliness/blob/master/rf_permutation_importances.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xbg_permutation_importances.png?raw=true)

Despite those differences, they produced very similar confusion matrices. Both were able to predict severe loneliness with a relatively high level of precision, still they tended to miss quite a few lonely people. Again Random Forest and XGB, respectively. 

![alt text](https://github.com/shainaboover/Loneliness/blob/master/rf_confusion_matrix.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xgb_confusion_matrix.png?raw=true)

I also found very similar, albeit, not great ROC curves

![alt text](https://github.com/shainaboover/Loneliness/blob/master/rf_roc_curve.png?raw=true)![alt text](https://github.com/shainaboover/Loneliness/blob/master/xgb_roc_curve.png?raw=true)

Lastly I checked the precision metric. Both models were able to predict loneliness much higher than baseline levels with Gradient Boosting performing slightly higher than Random Forest.

![alt text](https://github.com/shainaboover/Loneliness/blob/master/metrics_validation.png?raw=true)

This held true when run with the test set, though the accuracy scores dropped quite a bit.

![alt text](https://github.com/shainaboover/Loneliness/blob/master/xgb_report.png?raw=true)


While it is interesting to think about how our views of the world relate to our emotions around connection, it is still important to remember that loneliness is a highly subjective feeling that can change dramatically throughout life. If anything, these models reveal just a tiny bit about our perceptions of the world and our place in it. 

Do your own feelings of loneliness relate to any of the features listed? When we shine the light of consciousness onto our feelings and thought patterns, we can uncover deeper connections with ourselves and each other.
