# Introduction to Numpy and Array Operations

This document covers the basics of working with lists and numpy arrays in Python, including arithmetic operations, broadcasting, array properties, indexing, and slicing, with clear code examples and explanations.

---

## 1. Basic Python Operations

### Arithmetic with Variables

```python
x = 7
z = x * 2
print(z)
# Output: 14
```
- Assigns `7` to `x`, multiplies it by `2`, and prints the result.

### String Multiplication

```python
name = "Bipul"
print(name * 2)
# Output: BipulBipul
```
- Multiplying a string by an integer repeats the string.

### List Multiplication

```python
salaries = [5043, 6773, 7656, 2338, 4567]
print(salaries * 2)
# Output: [5043, 6773, 7656, 2338, 4567, 5043, 6773, 7656, 2338, 4567]
```
- Multiplying a list by an integer repeats the list contents, not the individual values.

---

## 2. Element-wise Operations

### Manual Element-wise Operation on List

```python
for salary in salaries:
  print(salary * 2)
# Output:
# 10086
# 13546
# 15312
# 4676
# 9134
```
- You need a loop to perform true element-wise operations on Python lists.

---

## 3. Using Numpy Arrays

### Creating and Printing Numpy Array

```python
import numpy as np

salaries = np.array([5043, 6773, 7656, 2338, 4567])
print(salaries)
# Output: [5043 6773 7656 2338 4567]
```
- Converts a list to a numpy array for efficient numerical operations.

### Element-wise Multiplication

```python
print(salaries * 2)
# Output: [10086 13546 15312  4676  9134]
```
- Multiplies each element by `2` directly.

---

## 4. Broadcasting

### Basic Broadcasting

```python
n2 = np.array([[2,3,4,1,6], [3,6,2,7,8], [2,6,8,9,5]])
print(n2 * 3)
# Output:
# [[ 6  9 12  3 18]
#  [ 9 18  6 21 24]
#  [ 6 18 24 27 15]]
```
- Each element of the array is multiplied by `3` (scalar broadcasted).

### Broadcasting with Same-length 1D Array

```python
n3 = np.array([2,3,2,3,2])
print(n2 * n3)
# Output:
# [[ 4  9  8  3 12]
#  [ 6 18  4 21 16]
#  [ 4 18 16 27 10]]
```
- The 1D array `n3` is broadcast across each row of `n2`.

### Broadcasting with Column Vector

```python
n4 = np.array([[2],[3],[2]])
print(n2 * n4)
# Output:
# [[ 4  6  8  2 12]
#  [ 9 18  6 21 24]
#  [ 4 12 16 18 10]]
```
- The column vector multiplies each corresponding row.

### Broadcasting Error Example

```python
n6 = np.array([[3,2,4,2,2], [2,4,3,2,2]])
print(n2 * n6)
# Raises ValueError: operands could not be broadcast together with shapes (3,5) (2,5)
```
- Arrays with incompatible shapes cannot be broadcast.

---

## 5. Array Properties

### 1D, 2D, and 3D Arrays

```python
a = np.array([4,3,5,6,1])
print(a.ndim)   # 1
print(a.shape)  # (5,)

b = np.array([[4,3,5,6,1]])
print(b.ndim)   # 2
print(b.shape)  # (1, 5)
```
- `.ndim` gives the number of dimensions.
- `.shape` gives the size along each dimension.

#### Example for 3D Array

```python
n3 = np.array([
  [[3,2,5,3,2],[3,2,4,3,2],[4,3,2,4,6]],
  [[2,1,3,1,2],[4,3,2,1,2],[4,5,6,7,8]]
])
print(n3.ndim)   # 3
print(n3.shape)  # (2, 3, 5)
print(n3.size)   # 30
```
- `.size` gives the total number of elements.

---

## 6. Indexing and Searching

### Single-element Indexing

```python
n1 = np.array([4,3,5,6,1])
print(n1[2])
# Output: 5

n2 = np.array([[3,2,5,3,2],[3,2,4,3,2],[4,3,2,4,6]])
print(n2[1,3])
# Output: 3
```

### Searching with `np.where`

```python
print(np.where(n1 == 6))
# Output: (array([3]),)

print(np.where(n2 == 2))
# Output: (array([0, 0, 1, 1, 2]), array([1, 4, 1, 4, 2]))
```
- Returns indices where the condition is true.

---

## 7. Slicing Arrays

### 1D Array Slicing

```python
n1 = np.array([4,3,5,6,1])
print(n1[1:4])   # [3 5 6]
print(n1[2:5])   # [5 6 1]
print(n1[2:])    # [5 6 1]
```

### 2D Array Slicing

```python
n2 = np.array([[3,2,5,3,2],[3,2,4,3,2],[4,3,2,4,6]])
print(n2[1:3, 1:4])
# Output:
# [[2 4 3]
#  [3 2 4]]

print(n2[:, 4:])
# Output:
# [[2]
#  [2]
#  [6]]
```

---

## Summary

- **Python lists** require loops for element-wise operations, while **numpy arrays** allow direct mathematical operations.
- **Broadcasting** is a powerful numpy feature enabling operations on arrays of different shapes.
- Numpy arrays have useful properties: `.ndim`, `.shape`, `.size`.
- Arrays can be indexed and sliced using intuitive Python syntax.
- Use `np.where` for searching in arrays.

For more examples and documentation, visit the official [Numpy documentation](https://numpy.org/doc/).

---
