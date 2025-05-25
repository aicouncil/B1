# Univariate and Bivariate Analysis in Pandas

This document provides definitions and practical examples of **univariate** and **bivariate** analysis as demonstrated in the notebook: [`ds_b1_pandas_3(Univariate&Bivariate_Analysis).ipynb`](https://github.com/aicouncil/B1/blob/main/Data_Science_3/ds_b1_pandas_3(Univariate%26Bivariate_Analysis).ipynb).

---

## Table of Contents

- [1. Introduction](#1-introduction)
- [2. Types of Data Analysis](#2-types-of-data-analysis)
- [3. Univariate Analysis](#3-univariate-analysis)
  - [3.1. On Categorical Data](#31-on-categorical-data)
  - [3.2. On Numerical Data](#32-on-numerical-data)
- [4. Bivariate Analysis](#4-bivariate-analysis)
  - [4.1. Categorical vs Categorical](#41-categorical-vs-categorical)
  - [4.2. Continuous vs Continuous](#42-continuous-vs-continuous)
  - [4.3. Categorical vs Continuous](#43-categorical-vs-continuous)
- [5. Example Dataset Columns](#5-example-dataset-columns)

---

## 1. Introduction

**Data analysis** is the process of inspecting, cleansing, transforming, and modeling data with the goal of discovering useful information and supporting decision-making. Two key approaches are univariate and bivariate analysis.

---

## 2. Types of Data Analysis

- **Univariate Analysis**: Analysis of a single variable at a time.
- **Bivariate Analysis**: Analysis of the relationship between two variables.
- **Multivariate Analysis**: Analysis involving more than two variables (not covered here).

---

## 3. Univariate Analysis

### Definition

Univariate analysis examines each variable individually to summarize and find patterns.

### 3.1. On Categorical Data

**Categorical Data**: Data that can be divided into specific groups or categories (e.g., product type, fat content).

#### Example: `Item_Identifier`

```python
df['Item_Identifier'].unique()
# Output: ['FD' 'DR' 'NC']

df['Item_Identifier'].value_counts()
# Output:
# FD    6125
# NC    1599
# DR     799
```

#### Example: `Item_Fat_Content`

```python
df['Item_Fat_Content'].unique()
# Output: ['low fat' 'regular']

df['Item_Fat_Content'].value_counts()
# Output:
# low fat    5517
# regular    3006
```

#### Example: `Item_Type`

```python
df['Item_Type'].unique()
# Output: Array of 16 item types (e.g., 'Dairy', 'Soft Drinks', 'Meat', ...)

df['Item_Type'].value_counts()
# Output (top 3 shown):
# Fruits and Vegetables    1232
# Snack Foods              1200
# Household                 910
# ...
```

---

### 3.2. On Numerical Data

**Numerical Data**: Data expressed as numbers (e.g., weights, prices).

#### Example: `Item_Weight`

```python
df['Item_Weight'].mean()
# Output: 12.8576

df['Item_Weight'].median()
# Output: 12.6
```

#### Example: `Item_MRP` (Maximum Retail Price)

```python
df['Item_MRP'].mean()
# Output: 140.99

df['Item_MRP'].median()
# Output: 143.01
```

---

## 4. Bivariate Analysis

### Definition

Bivariate analysis explores the relationship between two variables.

#### Types:

- Categorical vs Categorical
- Continuous vs Continuous
- Categorical vs Continuous

---

### 4.1. Categorical vs Categorical

**Example**: Relationship between `Item_Identifier` and `Item_Fat_Content` using a crosstab.

```python
pd.crosstab(df['Item_Identifier'], df['Item_Fat_Content'])
# Output:
# Item_Fat_Content  low fat  regular
# Item_Identifier
# DR                    728       71
# FD                   3190     2935
# NC                   1599        0
```

---

### 4.2. Continuous vs Continuous

While not shown explicitly in the notebook, this analysis typically investigates the correlation between two numerical variables, such as through a scatter plot or correlation coefficient.

**Example**: Examining the relationship between `Item_Weight` and `Item_MRP`.

---

### 4.3. Categorical vs Continuous

Although not shown explicitly, this involves comparing the distribution of a numerical variable across categories, often using groupby, boxplots, or bar charts.

**Example**: Average `Item_MRP` for each `Outlet_Type`.

```python
df.groupby('Outlet_Type')['Item_MRP'].mean()
```

---

## 5. Example Dataset Columns

| Column                    | Description                                      | Example Values        |
|---------------------------|--------------------------------------------------|----------------------|
| `Item_Identifier`         | Product code/category                            | FD, DR, NC           |
| `Item_Weight`             | Weight of product (numeric)                      | 9.3, 5.92            |
| `Item_Fat_Content`        | Fat content                                      | low fat, regular     |
| `Item_Visibility`         | Visibility percentage (numeric)                  | 0.016, 0.019         |
| `Item_Type`               | Product type/category                            | Dairy, Meat, Breads  |
| `Item_MRP`                | Maximum Retail Price (numeric)                   | 249.8, 48.2          |
| `Outlet_Identifier`       | Store code                                       | OUT049, OUT018       |
| `Outlet_Establishment_Year`| Year store was established                      | 1999, 2009           |
| `Outlet_Size`             | Store size (category)                            | High, Medium         |
| `Outlet_Location_Type`    | Store location tier                              | Tier 1, Tier 3       |
| `Outlet_Type`             | Store type                                       | Supermarket Type1     |
| `Item_Outlet_Sales`       | Sales value (numeric)                            | 3735.13, 443.42      |
| `quantity_sold`           | Number of items sold                             | 14, 9                |

---

## Summary

- **Univariate analysis**: Explore each variable individually, using `.value_counts()` for categorical and `.mean()`, `.median()` for numerical data.
- **Bivariate analysis**: Explore relationships between two variables, using cross-tabulation for categorical, and correlation/groupby for numerical.
- These methods are essential steps for data exploration before building models.

For more, see the original notebook: [ds_b1_pandas_3(Univariate&Bivariate_Analysis).ipynb](https://github.com/aicouncil/B1/blob/main/Data_Science_3/ds_b1_pandas_3(Univariate%26Bivariate_Analysis).ipynb)
