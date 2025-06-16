# Customer Churn Case Study Using Logistic Regression

This document explains how to solve a customer churn prediction problem with logistic regression, with a special focus on handling imbalanced data using techniques such as oversampling, threshold tuning, and class weight adjustment. Examples and code snippets are provided for clarity.

---

## Table of Contents

- [Problem Statement: What is Customer Churn?](#problem-statement-what-is-customer-churn)
- [Why is Data Imbalance a Problem?](#why-is-data-imbalance-a-problem)
- [Logistic Regression for Churn Prediction](#logistic-regression-for-churn-prediction)
- [Handling Imbalanced Data](#handling-imbalanced-data)
  - [1. Oversampling the Minority Class](#1-oversampling-the-minority-class)
  - [2. Threshold Tuning](#2-threshold-tuning)
  - [3. Class Weight Tuning](#3-class-weight-tuning)
- [Evaluation Metrics](#evaluation-metrics)
- [Summary Table](#summary-table)
- [Conclusion](#conclusion)

---

## Problem Statement: What is Customer Churn?

**Customer churn** is when a customer stops using a company's product or service. For businesses, predicting which customers are likely to churn is crucial for proactive retention strategies.

**Example**:  
A telecom company wants to predict which users will cancel their subscription next month based on their usage patterns, tenure, support calls, etc.

---

## Why is Data Imbalance a Problem?

In most churn datasets, the number of customers who churn is much lower than those who stay.  
**Example**:  
- 950 customers stayed (label 0)
- 50 customers churned (label 1)

If we train a model on this data, it could predict "no churn" for everyone and achieve 95% accuracy, but it would fail to identify churners.

---

## Logistic Regression for Churn Prediction

**Logistic Regression** is a classification algorithm used to estimate the probability that an observation belongs to a particular class (e.g., churn vs no churn).

**Basic Steps:**
1. Prepare your dataset (features and target variable).
2. Fit a logistic regression model.
3. Predict probabilities and classes.

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

---

## Handling Imbalanced Data

To improve model performance (especially recall for the minority class), we use several techniques:

### 1. Oversampling the Minority Class

**Oversampling** increases the number of minority class samples by duplicating existing ones or generating synthetic samples (e.g., with SMOTE).

**Example with Random Oversampling:**

```python
from imblearn.over_sampling import RandomOverSampler

ros = RandomOverSampler(random_state=42)
X_resampled, y_resampled = ros.fit_resample(X_train, y_train)
```

Now the number of churners and non-churners in the training set is equal, helping the model learn to detect churners better.

### 2. Threshold Tuning

By default, logistic regression uses a threshold of 0.5 to classify probabilities as class 1 ("churn") or 0 ("no churn"). With imbalanced data, lowering the threshold can help catch more churners.

**Example:**

```python
import numpy as np

# Predict probabilities
y_pred_proba = model.predict_proba(X_test)[:,1]

# Custom threshold
threshold = 0.3
y_pred_custom = (y_pred_proba > threshold).astype(int)
```

Lowering the threshold increases recall (detects more churners) but may reduce precision (more false positives).

### 3. Class Weight Tuning

Instead of oversampling, you can make the model *pay more attention* to the minority class by assigning it a higher weight.

**Example:**

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(class_weight={0:1, 1:10})
model.fit(X_train, y_train)
```

Alternatively, you can use `class_weight='balanced'` to let scikit-learn automatically adjust weights inversely proportional to class frequencies.

---

## Evaluation Metrics

With imbalanced data, overall accuracy is misleading. Instead, use:

- **Precision**: How many predicted churners actually churned?
- **Recall**: How many actual churners were detected?
- **F1 Score**: Harmonic mean of precision and recall.
- **ROC-AUC**: Measures model's ability to distinguish classes.

**Example:**

```python
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred_custom))
```

---

## Summary Table

| Step                   | Technique                  | Impact                                      |
|------------------------|----------------------------|----------------------------------------------|
| Baseline Model         | None                       | High accuracy, low recall for churners       |
| Oversampling           | Random/Synthetic           | Higher recall, possibly lower precision      |
| Threshold Tuning       | Lower cutoff (e.g., 0.3)   | Higher recall, lower specificity             |
| Class Weight Tuning    | `class_weight` param       | Higher recall, robust to imbalance           |

---

## Conclusion

- **Imbalanced data** is a major challenge in churn prediction.
- **Logistic regression** can be improved using oversampling, threshold tuning, and class weight adjustments.
- **Always use recall and precision** (not just accuracy) to evaluate models on imbalanced data.
- These techniques help businesses catch more potential churners, allowing for timely retention efforts.

---

**Further Reading:**
- [Imbalanced-learn documentation](https://imbalanced-learn.org/stable/)
- [Scikit-learn: Dealing with imbalanced classes](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html)
