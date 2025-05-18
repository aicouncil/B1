# Introduction to Pandas

**Pandas** is an open-source Python library used for data manipulation and analysis.  
It is especially powerful for working with structured data (tables, spreadsheets, etc.).

Pandas has two core data structures:
- **Series**: A one-dimensional labeled array (like a column in Excel).
- **DataFrame**: A two-dimensional labeled data structure (like a table).

---

## 1. Pandas Series

A **Series** is similar to a column in a spreadsheet. It has both data values and an index (labels).

### Example

```python
import pandas as pd

d1 = pd.Series([20, 32, 25, 19, 17], index=['a', 'b', 'c', 'd', 'e'])
print(d1)
```

**Output:**
```
a    20
b    32
c    25
d    19
e    17
dtype: int64
```

- The values are `[20, 32, 25, 19, 17]`.
- The index labels are `['a', 'b', 'c', 'd', 'e']`.

**Type Check:**

```python
print(type(d1))
```
Output:
```
<class 'pandas.core.series.Series'>
```

---

## 2. Creating Data with Dictionaries

You can organize data using Python dictionaries before converting them into a pandas DataFrame.

### Example

```python
emp_data = {
    "Name": ["Jai", "Arun", "Samjay", "Samir", "Ajay"],
    "Location": ["Jaipur", "Delhi", "Hyderabaad", "Chennai", "Indore"],
    "Age": [23, 25, 27, 21, 22]
}
print(emp_data)
```

**Output:**
```
{
  'Name': ['Jai', 'Arun', 'Samjay', 'Samir', 'Ajay'],
  'Location': ['Jaipur', 'Delhi', 'Hyderabaad', 'Chennai', 'Indore'],
  'Age': [23, 25, 27, 21, 22]
}
```

You can access any column (value list) by key:

```python
print(emp_data['Name'])
```
Output:
```
['Jai', 'Arun', 'Samjay', 'Samir', 'Ajay']
```

---

## 3. Pandas DataFrame

A **DataFrame** is like a table: each column is a Series, and each row has a label (index).

### Example

```python
d2 = pd.DataFrame(emp_data, index=['a', 'b', 'c', 'd', 'e'])
print(d2)
```

**Output:**

|   | Name   | Location    | Age |
|---|--------|-------------|-----|
| a | Jai    | Jaipur      | 23  |
| b | Arun   | Delhi       | 25  |
| c | Samjay | Hyderabaad  | 27  |
| d | Samir  | Chennai     | 21  |
| e | Ajay   | Indore      | 22  |

**Type Check:**
```python
print(type(d2))
```
Output:
```
<class 'pandas.core.frame.DataFrame'>
```

---

## 4. Accessing Data in DataFrames

You can select a column from a DataFrame using its column name.

### Example

```python
print(d2['Name'])
```

**Output:**
```
a       Jai
b      Arun
c    Samjay
d     Samir
e      Ajay
Name: Name, dtype: object
```

Notice that `d2['Name']` is a Series object:

```python
print(type(d2['Name']))
```
Output:
```
<class 'pandas.core.series.Series'>
```

---

## 5. Displaying the DataFrame

Simply typing the DataFrame name in a Jupyter notebook cell displays the table:

```python
d2
```

**Output:**

|   | Name   | Location    | Age |
|---|--------|-------------|-----|
| a | Jai    | Jaipur      | 23  |
| b | Arun   | Delhi       | 25  |
| c | Samjay | Hyderabaad  | 27  |
| d | Samir  | Chennai     | 21  |
| e | Ajay   | Indore      | 22  |

---

# Summary

- **Series**: One-dimensional labeled data, like a single column.
- **DataFrame**: Two-dimensional labeled data, like a table.
- Data can be created from dictionaries and accessed by columns or index.
- Each DataFrame column is a Series.
- Pandas is fundamental for data manipulation in Python.

---

**Tip:**  
Try modifying the values or index in the examples above and see how pandas behaves!
