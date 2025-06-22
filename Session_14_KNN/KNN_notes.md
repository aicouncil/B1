# K-Nearest Neighbors (KNN) Classification: Concepts and Data Preparation

This document provides a comprehensive overview of the K-Nearest Neighbors (KNN) classification algorithm, illustrating both manual implementation and data preparation steps with practical examples and explanations.

---

## 1. Introduction to KNN (K-Nearest Neighbors) Classification Algorithm

KNN is a simple, intuitive, and popular supervised machine learning algorithm used for classification (and sometimes regression) tasks. The algorithm classifies a new data point based on the majority label among its 'K' nearest neighbors in the feature space.

**How it works:**  
Given a value of K and a distance metric (commonly Euclidean distance), the algorithm finds the K training samples closest to the new point and assigns the most common class among them.

**Example Scenario:**  
Suppose you have three species of flowers and you want to classify a new flower based on its petal and sepal measurements. KNN will look at the K most similar flowers in your dataset and predict the species.

---

## 2. Data Import and Exploration

Before applying KNN, it's essential to load and explore your dataset.

**Step-by-step:**

1. **Import necessary libraries**
    ```python
    import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt
    ```
2. **Load the Iris dataset**
    ```python
    df = pd.read_csv('https://raw.githubusercontent.com/bipulshahi/Dataset/refs/heads/main/Iris.csv')
    ```
3. **Preview the data**
    ```python
    print(df.head())
    print(df.shape)
    ```

**Explanation:**  
- The dataset is loaded into a pandas DataFrame.
- The first few rows and the shape (number of rows and columns) are displayed to get an understanding of the data.

---

## 3. Preparing Data for KNN

To classify a new data point, you need a way to represent it and integrate it into your workflow.

**Example:**

1. **Defining a new flower data point**
    ```python
    new_flower = [0.3, 1.2, 1.2, 1.3]  # Example feature values
    ```

2. **Copying the dataset**
    ```python
    df1 = df.copy()
    ```

**Explanation:**  
- The new flower's features should match the features used in your dataset.
- Copying the dataset allows you to manipulate it (e.g., add new columns) without affecting the original data.

---

## 4. Manual Implementation of KNN Logic

KNN can be implemented from scratch by calculating the distance between the new data point and all points in the dataset.

**Step-by-step:**

1. **Calculate Euclidean distances**
    ```python
    x1 = df['SepalLengthCm']
    x2 = df['SepalWidthCm']
    x3 = df['PetalLengthCm']
    x4 = df['PetalWidthCm']

    df1['distances'] = np.sqrt(
        (x1 - new_flower[0])**2 +
        (x2 - new_flower[1])**2 +
        (x3 - new_flower[2])**2 +
        (x4 - new_flower[3])**2
    )
    ```
2. **Preview the updated dataset**
    ```python
    print(df1.head())
    ```

**Explanation:**  
- The Euclidean distance formula is used to measure similarity between the new point and each sample.
- The distances are stored in a new column, making it easy to identify the nearest neighbors.

---

## 5. Data Loading and Exploration (Wine Dataset Example)

KNN (and other algorithms) can also be applied to other datasets, such as the Wine dataset.

**Example:**

1. **Importing libraries**
    ```python
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    import seaborn as sns
    ```

2. **Loading and previewing the Wine dataset**
    ```python
    df = pd.read_csv('https://raw.githubusercontent.com/bipulshahi/Dataset/refs/heads/main/wine.csv')
    print(df.head())
    ```

3. **Examining target class distribution**
    ```python
    print(df['Target'].value_counts())
    ```

**Explanation:**  
- The Wine dataset is loaded and inspected.
- The target class distribution helps to understand if the dataset is balanced or imbalanced.

---

## 6. Feature and Target Preparation

For machine learning models, features (inputs) and targets (outputs) must be separated.

**Example:**

```python
X = df.drop(columns=['Target'])
y = df['Target']
```

**Explanation:**  
- `X` contains all feature columns.
- `y` contains the target variable for classification.

---

## 7. Feature Correlation Analysis

Understanding relationships between features helps in feature selection and understanding data redundancy.

**Example:**

```python
plt.figure(figsize=(10, 10))
sns.heatmap(X.corr(), annot=True, cmap='RdYlGn')
plt.show()
```

**Explanation:**  
- A heatmap visually represents correlations between features.
- Highly correlated features may provide redundant information.

---

## 8. Variance Inflation Factor (VIF) Calculation

VIF quantifies the severity of multicollinearity in regression analysis. High VIF indicates that a feature is highly correlated with other features.

**Step-by-step:**

1. **Add a constant to features**
    ```python
    import statsmodels.api as sm
    from statsmodels.stats.outliers_influence import variance_inflation_factor

    X_1 = sm.add_constant(X)
    ```

2. **Calculate VIF for each feature**
    ```python
    vif_df = pd.DataFrame()
    vif_df['variable'] = X_1.columns
    vif_df['VIF'] = [variance_inflation_factor(X_1.values, i) for i in range(X_1.shape[1])]
    print(vif_df)
    ```

**Explanation:**  
- VIF values above 5 or 10 indicate potential multicollinearity problems.
- Features with high VIF may need to be removed or combined.

---

## Summary

This guide introduces KNN classification, demonstrates manual distance calculations, and covers essential data exploration and preparation steps, including correlation analysis and multicollinearity checks (VIF). These practices are fundamental for building robust machine learning models.
