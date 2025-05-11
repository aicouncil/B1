# Session 3: Assignment Discussion & Advanced Python Functions

### Description
In this session, we explored key Python concepts to supercharge your coding skills! 📚✨

- **Assignment Review:** We analyzed your submissions, discussed challenges, and shared tips for improvement.
- **Deep Dive into Functions:** Learn how to handle dynamic arguments using `*args` and `**kwargs`.
- **Power Tools of Python:** Practical uses of `map()`, `filter()`, and `sorted()` to make your code cleaner and faster.
- **File Handling Basics:** How to read from and write to files effectively and safely.

---

## Assignment Review
### Highlights
- Addressed common challenges in the assignment.
- Shared tips to improve code readability and efficiency.
- Discussed alternative approaches to solving problems.

**Pro Tip:** Always test edge cases and document your code for better understanding.

---

## Deep Dive into Functions

### **`*args`**: Handling Variable-Length Positional Arguments
`*args` allows a function to accept any number of positional arguments.

#### Example:
```python
def sum_all(*args):
    return sum(args)

# Usage
print(sum_all(1, 2, 3, 4))  # Output: 10
```
#### Key Points:
- The `*args` parameter collects all extra positional arguments into a tuple.
- Useful when you don’t know beforehand how many arguments your function will receive.

---

### **`**kwargs`**: Handling Variable-Length Keyword Arguments
`**kwargs` allows a function to accept any number of keyword arguments.

#### Example:
```python
def greet_all(**kwargs):
    for name, message in kwargs.items():
        print(f"{name}: {message}")

# Usage
greet_all(Alice="Hello", Bob="Hi", Charlie="Good morning")
```
#### Key Points:
- The `**kwargs` parameter collects extra keyword arguments into a dictionary.
- Great for passing dynamic configurations to a function.

---

## Power Tools of Python

### **`map()`**: Applying a Function to a Sequence
The `map()` function applies a given function to every item in an iterable.

#### Example:
```python
def square(x):
    return x ** 2

numbers = [1, 2, 3, 4]
squared = list(map(square, numbers))
print(squared)  # Output: [1, 4, 9, 16]
```
#### Key Points:
- Returns a map object, so convert it to a list if needed.
- Ideal for transforming data without a loop.

---

### **`filter()`**: Filtering Items from a Sequence
The `filter()` function selects items from an iterable based on a condition.

#### Example:
```python
def is_even(x):
    return x % 2 == 0

numbers = [1, 2, 3, 4, 5, 6]
evens = list(filter(is_even, numbers))
print(evens)  # Output: [2, 4, 6]
```
#### Key Points:
- Only items that satisfy the condition are returned.
- Use for concise filtering logic.

---

### **`sorted()`**: Sorting Items in a Sequence
The `sorted()` function sorts items in a sequence and returns a new list.

#### Example:
```python
words = ["banana", "apple", "cherry"]
sorted_words = sorted(words)
print(sorted_words)  # Output: ['apple', 'banana', 'cherry']
```
#### Key Points:
- Can use the `key` argument to customize sorting.
- Supports reverse sorting with the `reverse=True` argument.

---

## File Handling Basics

### Reading from a File
#### Example:
```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```
#### Key Points:
- Use `with` to ensure the file is properly closed.
- Modes: `'r'` for reading, `'w'` for writing, `'a'` for appending.
- Handles files line by line or entirely based on requirements.

#### Advanced Example: Reading Specific Lines
```python
with open('example.txt', 'r') as file:
    lines = file.readlines()
    print(lines[0])  # Prints the first line
```
---

### Writing to a File
#### Example:
```python
with open('example.txt', 'w') as file:
    file.write("Hello, world!\n")
```
#### Key Points:
- Overwrites the file if it already exists.
- Use `'a'` mode to append instead of overwriting.

#### Advanced Example: Writing Multiple Lines
```python
with open('example.txt', 'w') as file:
    lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
    file.writelines(lines)
```

---

### File Modes Explained
#### Key Modes:
- `'a'`: Append mode. Adds new content to the end of the file without overwriting existing content.
    ```python
    with open('example.txt', 'a') as file:
        file.write("Appended text\n")
    ```
- `'x'`: Exclusive creation. Creates a new file and raises an error if it already exists.
    ```python
    try:
        with open('example.txt', 'x') as file:
            file.write("This file was created exclusively!\n")
    except FileExistsError:
        print("File already exists!")
    ```
- `'b'`: Binary mode. Used for reading or writing binary files, such as images or non-text data.
    ```python
    with open('example.jpg', 'rb') as file:
        content = file.read()
        print("Binary content read")
    ```

---

### Reading Line by Line
#### Example:
```python
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())
```
#### Key Points:
- Efficient for large files.
- Use `strip()` to remove newline characters.

#### Advanced Example: Searching for Keywords
```python
with open('example.txt', 'r') as file:
    for line in file:
        if "keyword" in line:
            print(line)
```

---

### Error Handling in File Operations
#### Example:
```python
try:
    with open('nonexistent.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("File not found. Please check the file path.")
```
#### Key Points:
- Always anticipate potential errors, like missing files or permission issues.
- Use `try-except` blocks to make file handling robust.

---

**Catch the recording now and boost your Python prowess! 🐍💡**
