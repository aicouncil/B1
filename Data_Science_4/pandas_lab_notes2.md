# Pandas Data Quality Exploration – Notes

This document summarizes all the key topics and code examples covered in the notebook [`ds_b1_pandas_2.ipynb`](https://github.com/aicouncil/B1/blob/main/Data_Science_4/ds_b1_pandas_2.ipynb). The focus is on understanding and assessing data quality using pandas.

---

## 1. Importing Essential Libraries

**Explanation:**  
To begin any data analysis task in Python, it’s important to import the necessary libraries.

**Example:**
```python
import pandas as pd      # For data manipulation
import numpy as np       # For numerical calculations
import matplotlib.pyplot as plt  # For data visualization
```

---

## 2. Reading the Dataset

**Explanation:**  
Pandas provides convenient functions to read data from various formats. In this case, an Excel file is loaded directly from a URL.

**Example:**
```python
df = pd.read_excel(
    'https://github.com/bipulshahi/Dataset/raw/refs/heads/main/bigmart.xlsx',
    index_col=0
)
df.head()  # Displays the first 5 rows
```

---

## 3. Understanding the Dataset Structure

**Explanation:**  
Viewing the dataset’s first few rows helps understand the data's structure, types, and sample values. Typical columns in the example dataset include:

- `Item_Identifier`
- `Item_Weight`
- `Item_Fat_Content`
- `Item_Visibility`
- `Item_Type`
- `Item_MRP`
- `Outlet_Identifier`
- `Outlet_Establishment_Year`
- `Outlet_Size`
- `Outlet_Location_Type`
- `Outlet_Type`
- `Item_Outlet_Sales`
- `quantity_sold`

---

## 4. Data Quality Assessment

### a. Data Types

**Explanation:**  
Checking data types ensures columns are in the expected format (numeric, categorical, etc.), which is crucial for further analysis.

**Example:**
```python
df.dtypes
```

### b. Missing Values

**Explanation:**  
Missing values can affect analysis, so identifying and handling them is a key step.

**Example:**
```python
df.isnull().sum()
```

### c. Outliers

**Explanation:**  
Outliers are extreme values that may distort statistical analyses and model predictions.

**Example:**
```python
df.describe()  # Helps spot unusual min/max values
```

### d. Multicollinearity

**Explanation:**  
Multicollinearity refers to highly correlated independent variables, which can impact regression models.

**Example:**
```python
df.corr()
```

### e. Skewness

**Explanation:**  
Skewness measures how much a distribution deviates from symmetry, which can affect statistical modeling.

**Example:**
```python
df.skew(numeric_only=True)
```

---

## 5. Data Dimensions

**Explanation:**  
Knowing the shape of the DataFrame helps understand the dataset size.

**Example:**
```python
df.shape  # Output: (number of rows, number of columns)
```

---

## 6. Selecting Numeric Columns

**Explanation:**  
Often, you need to work only with numeric columns (for statistical analysis, visualizations, etc.).

**Example:**
```python
df_num = df.select_dtypes(include='number')
df_num.head()
```

---

## 7. Selecting Non-Numeric (Categorical) Columns

**Explanation:**  
To analyze or preprocess categorical data, select columns that are not numeric.

**Example:**
```python
df_cat = df.select_dtypes(exclude='number')
df_cat.head()
```

---

## 8. Summary Table

| Topic                        | Purpose/Explanation                                   | Example Code                           |
|------------------------------|------------------------------------------------------|----------------------------------------|
| Import Libraries             | Access pandas, numpy, matplotlib                     | `import pandas as pd`                  |
| Read Data                    | Load data into DataFrame                             | `pd.read_excel(...)`                   |
| View Data                    | See sample data                                      | `df.head()`                            |
| Check Data Types             | Identify column types                                | `df.dtypes`                            |
| Check Missing Values         | Identify missing data                                | `df.isnull().sum()`                    |
| Detect Outliers              | Spot min/max values                                  | `df.describe()`                        |
| Check Multicollinearity      | Identify correlated variables                        | `df.corr()`                            |
| Check Skewness               | See if data is skewed                                | `df.skew(numeric_only=True)`           |
| Data Dimensions              | Dataset size                                         | `df.shape`                             |
| Select Numeric Columns       | Focus on numeric data                                | `df.select_dtypes(include='number')`   |
| Select Categorical Columns   | Focus on categorical data                            | `df.select_dtypes(exclude='number')`   |

---

## 9. Practical Tips

- Always check for missing and inconsistent data before analysis.
- Use visualization (e.g., histograms, boxplots) to further detect outliers and skewness.
- Convert data types where necessary (e.g., change object to category for categorical columns).
- Regularly use `df.info()` and `df.describe()` for quick dataset overviews.

---

**End of Notes**
