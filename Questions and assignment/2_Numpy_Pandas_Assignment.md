
# 📝 Assignment: Introduction to NumPy and Pandas

## 🟢 BASIC LEVEL

### Section 1: Introduction to NumPy

1. Create a NumPy array from the following list:  
   `list1 = [10, 20, 30, 40, 50]`  
   - Print the array.
   - Check its type and data type.

2. Create a 2D array using NumPy:  
   ```python
   [[1, 2, 3],
    [4, 5, 6]]
   ```  
   - Print the array and view its shape, size, and number of dimensions.

### Section 2: Element-wise Operations

3. Create two NumPy arrays:  
   `a = np.array([1, 2, 3])`  
   `b = np.array([4, 5, 6])`  
   - Perform addition, subtraction, and multiplication.
   - Show the element-wise multiplication result.

### Section 3: Pandas Introduction

4. What is Pandas? Briefly explain in your own words (3–4 lines).

5. Create a Pandas Series for the marks obtained in 3 subjects:  
   ```python
   subjects = ['Math', 'Physics', 'Chemistry']
   marks = [90, 85, 88]
   ```  
   - Create a Series with subject names as index.
   - Print the Series and check its type.

## 🟡 INTERMEDIATE LEVEL

### Section 4: Broadcasting in NumPy

6. Create the following arrays:  
   ```python
   A = np.array([[1, 2, 3], [4, 5, 6]])  
   B = np.array([1, 2, 3])
   ```  
   - Multiply A and B using broadcasting.
   - Explain in 2–3 lines how broadcasting works in this case.

7. Create two arrays:
   ```python
   C = np.array([[1, 2], [3, 4]])  
   D = np.array([1, 2, 3])
   ```
   - Try multiplying `C * D`. What happens?  
   - Write down the error message and explain why it occurs.

### Section 5: Indexing and Slicing

8. Given the array `arr = np.array([10, 20, 30, 40, 50, 60])`:
   - Slice elements from index 1 to 4.
   - Use slicing to get the last three elements.

9. Create a 2D array:
   ```python
   arr2d = np.array([[10, 20, 30, 40, 50],
                     [60, 70, 80, 90, 100],
                     [110, 120, 130, 140, 150]])
   ```
   - Slice elements from rows 1 to 2 and columns 1 to 3.
   - Use `np.where` to find the positions of values greater than 100.

### Section 6: Creating a DataFrame

10. Create a dictionary:
    ```python
    data = {
        'Name': ['Alice', 'Bob', 'Charlie'],
        'Age': [25, 30, 35],
        'City': ['Delhi', 'Mumbai', 'Bangalore']
    }
    ```
    - Convert it into a Pandas DataFrame.
    - Set custom indices: `['A', 'B', 'C']`
    - Print the DataFrame and its type.

## 🔴 ADVANCED LEVEL

### Section 7: Exploring Array Properties and Shapes

11. Create:
   - A 1D array of 6 elements
   - A 2D array of shape (3, 2)
   - A 3D array of shape (2, 2, 2)  
   For each, print:  
   - Number of dimensions (`ndim`)
   - Shape
   - Size

### Section 8: Valid and Invalid Broadcasting

12. Write 2 examples of valid broadcasting with explanations.

13. Write 1 example of invalid broadcasting:
   - Show code
   - Catch the ValueError
   - Explain why the shapes are not compatible

### Section 9: Accessing Data in DataFrames

14. Using the DataFrame from Q10:
   - Select the column `"City"` and display it.
   - Print the type of the selected column.
   - Display the entire DataFrame using `print()` and `.head()`.

15. Create a new DataFrame with at least 4 rows and 3 columns of your own data (e.g., student name, score, subject).
   - Access one full column and one specific row.
   - Use slicing to get the first 2 rows.

## ✅ Submission Instructions

- Submit your assignment as a **Jupyter Notebook (.ipynb)** or a **Python script (.py)**.
- Include **comments** in your code wherever necessary.
- Include **brief explanations** (as comments or markdown) for advanced questions.
