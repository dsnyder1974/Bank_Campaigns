# Bank Marketing Classifier Comparison

## Overview

This project compares several classification models to predict whether a customer will subscribe to a bank term deposit after a telephone marketing campaign. The dataset comes from the UCI Machine Learning Repository and includes results from 17 marketing campaigns conducted by a Portuguese banking institution. The main business objective is to help the bank improve future campaign efficiency by identifying customers who are more likely to respond positively, reducing wasted outreach, and supporting better marketing decisions.

The models compared in this analysis were:

- Logistic Regression
- K Nearest Neighbors
- Decision Tree
- Support Vector Machine

The data was preprocessed by encoding categorical variables and scaling numeric variables where appropriate. The target variable was whether the customer subscribed to a term deposit.

## Key Findings

The dataset is highly imbalanced, with most customers not subscribing to a term deposit. Because of this, accuracy alone was not enough to evaluate model performance. F1 score was also used because it balances precision and recall and gives a better sense of how well each model identifies the smaller group of customers who actually subscribed.

The Decision Tree model produced the strongest overall results. It had the highest testing accuracy and the highest F1 score, suggesting that it performed best at identifying likely subscribers while still maintaining strong overall accuracy.

The analysis also found that some important features, such as `nr.employed`, `pdays`, `cons.conf.idx`, and `euribor3m`, contributed strongly to the model’s predictions. However, several of these are broader economic indicators rather than direct customer traits, so they are more useful for understanding campaign timing and context than for directly choosing individual customers.

The `duration` feature should be excluded from a realistic predictive model because it is only known after a call has already occurred. Including it would create data leakage and would not support the business goal of predicting customer behavior before contact.

## Model Performance

| Model | Train Accuracy | Test Accuracy | F1 Score |
|---|---:|---:|---:|
| Logistic Regression | 0.900486 | 0.901797 | 0.334156 |
| KNN | 0.902944 | 0.901190 | 0.351911 |
| Decision Tree | 0.903065 | 0.902646 | 0.375389 |
| SVM | 0.904856 | 0.903496 | 0.362470 |

The Decision Tree was the best-performing model based on the combination of test accuracy and F1 score. KNN achieved perfect training accuracy, but its lower testing accuracy and F1 score suggest overfitting. Logistic Regression and SVM both performed well in terms of accuracy, but their lower F1 scores indicate that they were less effective than the Decision Tree at identifying positive subscription cases.

## Recommendations

The bank should consider using the tuned Decision Tree model as a starting point for identifying customers who are more likely to subscribe to a term deposit. This model provided the strongest balance of accuracy, F1 score, and interpretability, making it useful for both prediction and business explanation.

Because the business goal is to improve campaign targeting, the bank should pay close attention to false negatives and false positives. False negatives represent missed opportunities where the model failed to identify a customer who may have subscribed. False positives represent customers who may be contacted even though they are unlikely to subscribe, which can increase campaign costs.

The bank should also use the model’s most important features carefully. Economic indicators may help determine when campaigns are more likely to succeed, while customer and campaign history variables, such as previous contact behavior, may be more useful for deciding who to contact.

Future improvements could include adjusting the classification threshold, testing additional metrics such as recall and precision, and exploring more customer-level features to make the model more actionable for marketing teams.