# Data Quality Assessment and Exploration with Pandas

This tutorial demonstrates essential steps in data quality assessment and initial exploration using the Pandas library in Python. It covers loading data, examining its structure, and preparing it for further analysis by focusing on data types, missing values, outliers, multicollinearity, and skewness.

---

## 1. Getting Started: Import Libraries

Begin by importing the necessary libraries for data manipulation and visualization.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

---

## 2. Loading the Dataset

Read the dataset directly from a remote URL (Excel format) into a Pandas DataFrame.

```python
df = pd.read_excel('https://github.com/bipulshahi/Dataset/raw/refs/heads/main/bigmart.xlsx', index_col=0)
df.head()
```

**Sample Output:**

|   | Item_Identifier | Item_Weight | Item_Fat_Content | Item_Visibility | Item_Type           | Item_MRP | Outlet_Identifier | ... | quantity_sold |
|---|-----------------|-------------|------------------|-----------------|---------------------|----------|-------------------|-----|---------------|
| 0 | FD              | 9.30        | low fat          | 0.016047        | Dairy               | 249.8092 | OUT049            | ... | 14            |
| 1 | DR              | 5.92        | regular          | 0.019278        | Soft Drinks         | 48.2692  | OUT018            | ... | 9             |
| 2 | FD              | 17.50       | low fat          | 0.016760        | Meat                | 141.6180 | OUT049            | ... | 14            |
| ... | ...           | ...         | ...              | ...             | ...                 | ...      | ...               | ... | ...           |

---

## 3. Data Quality Assessment

### What do we check?

- **Data Types**: Ensure columns have appropriate data types (numeric, categorical, etc.).
- **Missing Values**: Check for and handle empty or null entries.
- **Outliers**: Identify values that are outside the expected range.
- **Multicollinearity**: Detect highly correlated features.
- **Skewness**: Check if data distribution is biased or asymmetrical.

---

## 4. Basic Data Exploration

### A. Dataset Shape

Check how many rows and columns are present.

```python
print(df.shape)
# Output: (8523, 13)
```
*This means there are 8,523 rows and 13 columns.*

---

### B. Data Types

Examine the data types for each column.

```python
print(df.dtypes)
```

**Sample Output:**

```
Item_Identifier               object
Item_Weight                  float64
Item_Fat_Content              object
Item_Visibility              float64
Item_Type                     object
...
quantity_sold                  int64
```

*Object types usually represent categorical/string data, while float64 and int64 are for numerical data.*

---

## 5. Separating Data by Type

### A. Numeric Columns

Select only the numeric columns for analysis.

```python
df_num = df.select_dtypes(include='number')
df_num.head()
```

|   | Item_Weight | Item_Visibility | Item_MRP | ... | quantity_sold |
|---|-------------|-----------------|----------|-----|---------------|
| 0 | 9.30        | 0.016047        | 249.8092 | ... | 14            |
| ... | ...       | ...             | ...      | ... | ...           |

### B. Categorical Columns

Select only the categorical (non-numeric) columns.

```python
df_cat = df.select_dtypes(exclude='number')
df_cat.head()
```

|   | Item_Identifier | Item_Fat_Content | Item_Type           | ... |
|---|-----------------|------------------|---------------------|-----|
| 0 | FD              | low fat          | Dairy               | ... |
| ... | ...           | ...              | ...                 | ... |

---

## 6. Example: Checking Missing Values

Check for missing values in each column:

```python
print(df.isnull().sum())
```

*This command shows the number of missing values in each column.*

---

## 7. Example: Detecting Outliers

A simple way to check for outliers in numeric columns:

```python
for col in df_num.columns:
    plt.figure()
    df_num.boxplot([col])
    plt.title(f'Boxplot of {col}')
    plt.show()
```

*Boxplots can visually highlight outliers as points outside the whiskers.*

---

## 8. Example: Checking for Multicollinearity

Calculate the correlation matrix:

```python
corr = df_num.corr()
print(corr)
```

*High correlation values (close to 1 or -1) between features indicate potential multicollinearity.*

---

## 9. Example: Checking Skewness

Calculate skewness for each numeric column:

```python
print(df_num.skew())
```

*Values outside the range of -1 to 1 often indicate skewed distributions.*

---

## Conclusion

This tutorial covered the first steps in data quality assessment and exploration using Pandas, including:

- Loading data from an external source
- Examining structure and data types
- Separating numeric and categorical columns
- Performing fundamental checks for data quality

These steps are essential before moving to deeper analysis, modeling, or visualization in any data science project.

---
