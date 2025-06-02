# Machine Learning Concepts Explained — Linear and Non-Linear Regression

This document explains the key topics and concepts covered in the notebook `ds_b1_ml_2.ipynb`, including data analysis, linear regression, non-linear regression, and practical examples using datasets. Each section is accompanied by code and explanations to help you understand how these machine learning approaches are applied in practice.

---

## 1. Introduction to the Advertising Dataset

The notebook starts by loading a classic advertising dataset, which contains data on TV, radio, and newspaper advertising budgets and their impact on sales.

```python
import pandas as pd
import numpy as np

df = pd.read_csv('https://github.com/bipulshahi/Dataset/raw/refs/heads/main/Advertising.csv', index_col=0)
df.head()
```

**Sample Data:**

| TV    | radio | newspaper | sales |
|-------|-------|-----------|-------|
| 230.1 | 37.8  | 69.2      | 22.1  |
| 44.5  | 39.3  | 45.1      | 10.4  |
| ...   | ...   | ...       | ...   |

**Explanation:**  
Each row represents a market, and columns show the amount spent on advertising via TV, radio, and newspapers, along with the corresponding sales.

---

## 2. Data Exploration and Cleaning

### 2.1. Data Types

Check the data types to confirm that all features are numeric:

```python
df.dtypes
```
All columns are of type `float64`, suitable for regression analysis.

### 2.2. Missing Values

Check for missing values in the dataset:

```python
df.isna().sum()
```
**Result:**  
No missing values in any column.

---

## 3. Exploratory Data Analysis (EDA)

### 3.1. Correlation Analysis

Visualize how each feature correlates with others using a heatmap:

```python
import seaborn as sns
sns.heatmap(df.corr(), annot=True, fmt='.2f', cmap='RdYlGn')
```

**Explanation:**  
- High correlation between TV and sales indicates TV advertising has a strong impact on sales.
- Lower correlations for radio and newspaper suggest weaker effects.

### 3.2. Pairplot

Pairwise relationships between variables:

```python
sns.pairplot(df)
```
**Explanation:**  
This allows us to visually inspect linear and non-linear relationships between features and the target variable.

---

## 4. Linear Regression

### 4.1. Preparing Data

Select features and target variable:

```python
X = df[['TV','radio']]
y = df['sales']

from sklearn.model_selection import train_test_split
xtrain, xtest, ytrain, ytest = train_test_split(X, y)
```

### 4.2. Training the Model

```python
from sklearn.linear_model import LinearRegression

modelA = LinearRegression()
modelA.fit(xtrain, ytrain)
```

### 4.3. Evaluating the Model

```python
ytrain_pred = modelA.predict(xtrain)
ytest_pred = modelA.predict(xtest)

mae_train = abs(ytrain - ytrain_pred).mean()
mae_test = abs(ytest - ytest_pred).mean()

print("Train mean absolute error", mae_train)
print("Test mean absolute error", mae_test)
```

**Explanation:**  
- The mean absolute error (MAE) gives us an idea of how far off our predictions are from the true values on average.
- Lower MAE means better model performance.

---

## 5. Non-Linear Regression

### 5.1. Visualizing Non-Linearity

Let's create a simple synthetic dataset:

```python
x1 = np.array([3,5,2,7,9]).reshape(5,1)
y1 = np.array([4,6,3,8,7]).reshape(5,1)

import matplotlib.pyplot as plt
plt.scatter(x1, y1)
plt.show()
```

### 5.2. Fitting a Linear Model

```python
from sklearn.linear_model import LinearRegression
model_linear = LinearRegression()
model_linear.fit(x1, y1)

yp1 = model_linear.predict(x1)

plt.scatter(x1, y1)
plt.plot(x1, yp1, 'r')
plt.show()
```

**Explanation:**  
The linear fit (red line) may not capture the true pattern if the relationship is non-linear.

### 5.3. Polynomial Regression

To capture non-linear patterns, transform the original features into polynomial features.

#### Degree 2 Polynomial

```python
from sklearn.preprocessing import PolynomialFeatures
pol = PolynomialFeatures(degree=2, include_bias=False)
pol.fit(x1)
x1_pol = pol.transform(x1)
```

**Transformed Data Example:**

| x1 | x1^2 |
|----|------|
| 3  | 9    |
| 5  | 25   |
| ...| ...  |

Fit a linear model using the polynomial features:

```python
model_linear.fit(x1_pol, y1)
x_new = np.linspace(2,9).reshape(-1,1)
x_new_pol = pol.transform(x_new)
yp1 = model_linear.predict(x_new_pol)

plt.scatter(x1, y1)
plt.plot(x_new, yp1, 'r')
plt.show()
```

#### Degree 3 Polynomial

```python
pol = PolynomialFeatures(degree=3, include_bias=False)
pol.fit(x1)
x1_pol_3 = pol.transform(x1)
model_linear.fit(x1_pol_3, y1)
x_new_pol = pol.transform(x_new)
yp1 = model_linear.predict(x_new_pol)

plt.scatter(x1, y1)
plt.plot(x_new, yp1, 'r')
plt.show()
```

**Explanation:**  
- Polynomial regression fits a curve rather than a straight line.
- The degree of the polynomial controls the model's flexibility.

---

## 6. Example: Salary Dataset

### 6.1. Load and View Data

```python
df_salary = pd.read_csv('https://github.com/bipulshahi/Dataset/raw/refs/heads/main/Salary_dataset.csv', index_col=0)
df_salary.head()
```

| YearsExperience | Salary   |
|-----------------|----------|
| 1.2             | 39344.0  |
| 1.4             | 46206.0  |
| ...             | ...      |

### 6.2. Comparing Linear and Non-Linear Regression

- **Linear Regression:** Fits a straight line to predict Salary from Years of Experience.
- **Polynomial Regression:** Fits a curve (e.g., quadratic or cubic) to capture non-linear relationships.

**Typical Steps:**
- Visualize data with a scatter plot.
- Fit a linear model and visualize the fit.
- Fit polynomial models of higher degrees and visualize.
- Compare MAE or another error metric for both models.

---

## 7. Summary

- **Linear Regression:** Best for relationships that are approximately linear.
- **Non-Linear (Polynomial) Regression:** Use for curvilinear relationships where data cannot be well-approximated by a straight line.
- **Model Selection:** Compare models using error metrics (e.g., MAE) and visual inspection.

---

## 8. Key Takeaways

- Always visualize your data to understand relationships.
- Start with simple models and increase complexity as needed.
- Avoid overfitting by not choosing overly complex models for small datasets.

---

**References:**
- [Advertising Dataset](https://github.com/bipulshahi/Dataset/blob/main/Advertising.csv)
- [Salary Dataset](https://github.com/bipulshahi/Dataset/blob/main/Salary_dataset.csv)
