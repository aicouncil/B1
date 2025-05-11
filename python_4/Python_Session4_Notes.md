# Python Fundamentals: Key Concepts and Practical Demonstrations

## Description
This session covers the foundational principles of Python programming, including robust error handling, Object-Oriented Programming (OOP), and an introduction to essential libraries for Data Science. Practical demonstrations ensure a hands-on understanding of each topic. 🐍✨

---

## Exception Handling

### **Understanding `try-except` Blocks**
Exception handling in Python allows you to manage errors gracefully, ensuring your program doesn't crash unexpectedly.

#### Example:
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Division by zero is not allowed!")
```

### **Handling Specific and General Exceptions**
You can target specific exceptions or use a general `except` block for unforeseen errors.

#### Example:
```python
try:
    with open('nonexistent_file.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("The file does not exist!")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

### **Real-World Use Case: File Operations**
```python
def read_file(filepath):
    try:
        with open(filepath, 'r') as file:
            return file.read()
    except FileNotFoundError:
        print("Please check if the file path is correct.")
    except PermissionError:
        print("Permission denied! Unable to access the file.")
```

---

## Object-Oriented Programming (OOP)

### **Introduction to Classes and Objects**
Classes are blueprints for objects, and objects are instances of classes.

#### Example:
```python
class Dog:
    def bark(self):
        return "Woof!"

my_dog = Dog()
print(my_dog.bark())  # Output: Woof!
```

### **Defining Attributes and Methods**
Attributes store data, and methods define behaviors for a class.

#### Example:
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def start(self):
        return f"{self.brand} {self.model} is starting."

my_car = Car("Toyota", "Corolla")
print(my_car.start())
```

### **Using Constructors (`__init__`)**
The `__init__` method initializes object attributes during object creation.

### **Real-World Examples**
#### Visitor Details:
```python
class Visitor:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, {self.name}! You are {self.age} years old."

visitor = Visitor("Alice", 30)
print(visitor.greet())
```

#### Employee Class:
```python
class Employee:
    def __init__(self, name, position):
        self.name = name
        self.position = position

    def show_details(self):
        return f"Employee: {self.name}, Position: {self.position}"

emp = Employee("John", "Developer")
print(emp.show_details())
```

#### Calculator Class:
```python
class Calculator:
    def add(self, x, y):
        return x + y

calc = Calculator()
print(calc.add(5, 7))  # Output: 12
```

---

## Introduction to Python Libraries for Data Science

### **Overview of Key Libraries**
1. **Numpy:** Numerical operations on large arrays and matrices.
2. **Pandas:** Data manipulation and analysis.
3. **Matplotlib:** Data visualization.

---

## Numpy Basics

### **Creating and Manipulating Arrays**
#### Example:
```python
import numpy as np
arr = np.array([1, 2, 3, 4])
print(arr)  # Output: [1 2 3 4]
```

### **Basic Mathematical Operations**
#### Example:
```python
arr = np.array([1, 2, 3])
print(arr + 10)  # Output: [11 12 13]
```

### **Using Aggregate Functions**
#### Example:
```python
arr = np.array([1, 2, 3, 4])
print(np.sum(arr))  # Output: 10
print(np.mean(arr))  # Output: 2.5
```

### **Operations Along Specific Axes**
#### Example:
```python
matrix = np.array([[1, 2], [3, 4]])
print(np.sum(matrix, axis=0))  # Output: [4 6] (column-wise sum)
print(np.sum(matrix, axis=1))  # Output: [3 7] (row-wise sum)
```

---

**Explore the recording to dive deeper into these topics and enhance your Python skills! 🚀**
