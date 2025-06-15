# Session 12: Logistic Regression – Detailed Explanation & Case Study

This document explains the step-by-step process and code covered in the notebook `ds_b1_logistic_regression_1.ipynb`, including a real-world case study on **Customer Churn Prediction**.

---

## Table of Contents

1. [Introduction to Logistic Regression](#introduction-to-logistic-regression)
2. [Numerical Exploration: Exponential Function](#numerical-exploration-exponential-function)
3. [Synthetic Data Creation](#synthetic-data-creation)
4. [Combining Features and Labels](#combining-features-and-labels)
5. [Building a Linear Model](#building-a-linear-model)
6. [The Sigmoid Function](#the-sigmoid-function)
7. [Prediction Function](#prediction-function)
8. [Making Predictions and Interpreting Output](#making-predictions-and-interpreting-output)
9. [Manual Gradient Descent Training](#manual-gradient-descent-training)
10. [Case Study: Customer Churn Prediction](#case-study-customer-churn-prediction)
11. [Summary & Further Exploration](#summary--further-exploration)

---

## Introduction to Logistic Regression

Logistic regression is a fundamental machine learning technique for binary classification problems. It predicts the probability that a given data point belongs to a particular class. The key idea is to map a linear combination of inputs to a probability using the **sigmoid function**.

---

## Numerical Exploration: Exponential Function

```python
import numpy as np
a = 56
np.exp(a)
```
- Calculates \( e^{56} \), a very large number (~2.09e+24).

```python
a = -12
np.exp(a)
```
- Calculates \( e^{-12} \), a very small number (~6.14e-6).

**Purpose:**  
Understanding the behavior of the exponential function is important since the sigmoid function (used in logistic regression) is based on exponentials.

---

## Synthetic Data Creation

We create artificial data to simulate a binary classification scenario (e.g., predicting customer churn).

```python
a1 = np.random.randint(1, 15, size=(5, 1))    # Group 1 (non-churned)
a2 = np.random.randint(15, 35, size=(5, 1))   # Group 2 (churned)
features = np.vstack((a1, a2))
```

- **a1:** 5 samples with smaller values (simulate non-churned customers).
- **a2:** 5 samples with larger values (simulate churned customers).
- **features:** 10x1 array, stacking both groups.

**Example Output:**
```
[[ 2]
 [ 6]
 [ 5]
 [11]
 [ 1]
 [25]
 [20]
 [24]
 [30]
 [20]]
```

### Creating Labels

```python
y = np.array([0,0,0,0,0,1,1,1,1,1]).reshape(10,1)
```
- First 5 are `0` (not churned), last 5 are `1` (churned).

---

## Combining Features and Labels

```python
data = np.hstack((features, y))
print(data)
```
- Combines features and labels into a single 10x2 array.
- Each row: `[feature, label]`.

**Example Output:**
```
[[ 2  0]
 [ 6  0]
 [ 5  0]
 [11  0]
 [ 1  0]
 [25  1]
 [20  1]
 [24  1]
 [30  1]
 [20  1]]
```

---

## Building a Linear Model

```python
w0 = 1
w1 = 1
yh = w0 + w1 * data[:,0:1]
```
- Linear hypothesis: \( y_{\text{hat}} = w_0 + w_1 \times x \)
- For each input value, computes the linear "score".

**Example:**  
If `x = 2`, then \( y_{\text{hat}} = 1 + 1 \times 2 = 3 \).

---

## The Sigmoid Function

The sigmoid function maps any real value to a value between 0 and 1 (interpreted as a probability):

\[
\sigma(z) = \frac{1}{1 + e^{-z}}
\]

**Code Example:**
```python
for val in yh:
    print(1 / (1 + np.exp(-val)))
```

- For large positive values, output ≈ 1
- For large negative values, output ≈ 0
- For 0, output = 0.5

---

## Prediction Function

```python
from math import exp

def predict(row, coef):
    yh = coef[0] + coef[1] * row[0]
    return 1.0 / (1.0 + exp(-yh))
```
- Takes a data row and coefficient list.
- Outputs the probability (between 0 and 1) for the positive class.

---

## Making Predictions and Interpreting Output

```python
coef = [0.56, 0.32]
for row in data:
    z = predict(row, coef)
    print(f"Expected={row[1]}, Calculated={z}, Predicted={round(z)}")
```

- Prints the actual label, predicted probability, and the rounded prediction (0 or 1).
- **Note:** Initial coefficients may not yield correct predictions.

---

## Manual Gradient Descent Training

Manually updates the model coefficients using gradient descent to minimize prediction error.

```python
lr = 0.01
coef = [0.56, 0.32]

for i in range(1000):
    sum_error = 0
    for row in data:
        z = predict(row, coef)
        error = row[1] - z
        sum_error += error**2
        coef[0] += lr * 2 * error * z * (1-z)
        coef[1] += lr * 2 * error * z * (1-z) * row[0]
    print(i, sum_error)
```

- **lr:** Learning rate (controls step size).
- **coef[0], coef[1]:** Bias and weight, updated each iteration.
- **sum_error:** Tracks total squared error per epoch.
- Coefficients improve over time, error decreases.

---

## Case Study: Customer Churn Prediction

### Problem Definition

Given customer data, predict if a customer will **churn** (leave the service).

### Mapping the Example

- **Features:** Could represent the number of customer support calls, usage frequency, etc.
- **Labels:** 0 = Not churned, 1 = Churned

**Data Generation in Notebook:**
- Customers with smaller feature values are labeled as not churned (0).
- Customers with larger feature values are labeled as churned (1).

### Logistic Regression Application

- The model learns a relationship between customer features and likelihood to churn.
- The sigmoid function outputs the churn probability for each customer.
- The gradient descent optimizes the model parameters to improve prediction accuracy.

### Real-World Application

In an actual business scenario:
- There would be many features per customer.
- Data would be split into training and test sets.
- Model performance would be evaluated using metrics like accuracy, recall, precision, ROC-AUC, etc.
- Insights from the model would help the business target at-risk customers and reduce churn.

---

## Summary & Further Exploration

**Key Concepts Covered:**
- Exponential and sigmoid function behavior
- Creating and labeling synthetic data
- Linear model construction
- Probability prediction with the sigmoid function
- Manual logistic regression prediction
- Training with gradient descent
- Application to customer churn prediction

**To Try Next:**
- Use real datasets with more features.
- Explore logistic regression with `scikit-learn`.
- Evaluate model performance with classification metrics.
- Visualize decision boundaries and probabilities.

---

**End of Session 12 Explanation**
