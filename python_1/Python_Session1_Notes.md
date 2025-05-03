## Python Basics - Detailed Trainer Notes (Session 1)

Welcome to Python! This document covers everything explained in your first 2.5-hour session, designed for absolute beginners. Each topic is explained in a simple, relatable, and example-rich way—like a friendly trainer guiding you step by step.

---

### 1. What is Python?

**Python** is a high-level, general-purpose programming language.

- **High-level** means it’s closer to human language, making it easy to read and write.
- **General-purpose** means it can be used for many things like web development, automation, data analysis, machine learning, and more.

#### Example:
If programming languages were people:
- C is a strict school teacher.
- Java is a corporate employee in a suit.
- Python is that chill friend who gets the job done in pajamas.

```python
print("Hello, world!")
```
One line. That’s all it takes to display something in Python!

---

### 2. Requirements of Python

To start using Python, you need:
1. A computer or laptop
2. Internet connection (for downloading Python and tools)
3. Python installed

That's it! No fancy licenses. Python is open-source and free.

**Pro Tip:** Python works on Windows, macOS, and Linux.

---

### 3. Python Interpreter

A Python **interpreter** is the software that reads and executes your Python code.

When you write:
```python
2 + 3
```
The interpreter reads it, understands what you mean, and gives the result: `5`.

You can run the interpreter in a terminal/command prompt by typing:
```bash
python
```
You’ll see something like:
```bash
>>>
```
This is where you can try out code line by line (called the REPL: Read-Eval-Print Loop).

---

### 4. Python IDLE

IDLE = **Integrated Development and Learning Environment**

It comes pre-installed with Python. It has two parts:
- Shell (interactive mode)
- Script editor (for saving files)

You can open it from the Start Menu (Windows) or search "IDLE".

**Example: Write this in IDLE and run it:**
```python
name = "Alice"
print("Hello,", name)
```

---

### 5. Jupyter Notebook

Jupyter is like an interactive notebook.
- You can write code, explanations, and outputs all in one place.
- Very popular in data science and machine learning.

To run Jupyter:
```bash
pip install notebook
jupyter notebook
```

This opens in your browser.

**Example Cell:**
```python
x = 10
y = 20
print("Sum:", x + y)
```

---

### 6. Variables and Values

A **variable** is a name that stores a value.
Think of it like a labeled box.

```python
age = 25
name = "Bob"
pi = 3.14
```

Rules for variable names:
- Must start with a letter or underscore
- Can contain letters, numbers, underscores
- Can’t use keywords like `if`, `class`, `def`

**Funny Example:**
```python
dog_name = "Bruno"
print("My dog is", dog_name)
```

---

### 7. Operators

Operators perform operations on values/variables.

#### Arithmetic Operators:
```python
2 + 3     # 5
4 - 1     # 3
5 * 2     # 10
10 / 2    # 5.0
5 % 2     # 1 (remainder)
2 ** 3    # 8 (exponent)
```

#### Comparison Operators:
```python
5 > 3     # True
2 == 2    # True
4 != 5    # True
```

#### Logical Operators:
```python
True and False   # False
True or False    # True
not True         # False
```

---

### 8. Data Types

Python has several **data types**:

#### Numbers
- **int**: whole numbers → 10, -3
- **float**: decimal numbers → 3.14, -7.8

#### Strings
- Text inside quotes
```python
"hello", 'world'
```
- Combine strings:
```python
"AI" + "Council"  # 'AICouncil'
```

#### Boolean
- True or False
```python
is_raining = False
```

#### Type Checking
```python
type(3.14)    # <class 'float'>
type("Hi")    # <class 'str'>
```

---

### 9. Conditional Programming

Conditional statements help Python make decisions.

#### if statement:
```python
age = 20
if age >= 18:
    print("You can vote!")
```

#### if-else:
```python
num = 5
if num % 2 == 0:
    print("Even")
else:
    print("Odd")
```

#### if-elif-else:
```python
marks = 85
if marks >= 90:
    print("Grade A")
elif marks >= 75:
    print("Grade B")
else:
    print("Grade C")
```

**Funny Example:**
```python
hungry = True
if hungry:
    print("Eat samosa")
else:
    print("Keep coding")
```

---

Let me know if you’d like diagrams, quizzes, or hands-on practice questions for each topic!
