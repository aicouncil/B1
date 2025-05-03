# Python Basics 

## Part 1: Getting Started with Python

### 1. What is Python and Why is it Widely Used?

**Python** is a high-level, general-purpose programming language created by Guido van Rossum in 1991. It is popular for its simplicity, versatility, and powerful libraries.

#### Key Features:
- **Easy to Learn**: Python's syntax is clean and intuitive.
- **Versatile**: Can be used for web development, data science, automation, AI, and more.
- **Extensive Libraries**: Libraries like Pandas, NumPy, TensorFlow, etc., cater to various needs.
- **Community Support**: A large and active community provides ample resources and assistance.

#### Example:
```python
print("Hello, World!")
```

### 2. Requirements and Setup for Python Programming

#### Step 1: Install Python
1. Download the latest version of Python from [python.org/downloads](https://www.python.org/downloads).
2. During installation:
   - Check the box "Add Python to PATH".
   - Complete the installation.

#### Step 2: Verify Installation
Open a terminal or command prompt and type:
```bash
python --version
```

#### Optional Tools:
- **VS Code**: A lightweight and powerful code editor.
- **PyCharm**: An IDE tailored for Python development.

### 3. Understanding the Python Interpreter and Python IDLE

#### Python Interpreter:
The interpreter executes Python commands interactively. Open a terminal and type:
```bash
python
```
Enter Python commands, and they will be executed immediately.

#### Python IDLE:
A built-in Python environment for writing and testing scripts. Access it via your system menu. Example:
```python
name = "Python"
print(f"Welcome to {name}!")
```

### 4. Introduction to Jupyter Notebook

#### Installation:
1. Install Anaconda from [anaconda.com](https://www.anaconda.com/).
   - Includes Jupyter Notebook and other tools.
2. Alternatively, use pip:
```bash
pip install notebook
```

#### Starting Jupyter Notebook:
1. Open a terminal and type:
```bash
jupyter notebook
```
2. A browser will open with the Jupyter interface.

#### Creating and Running Code:
1. Click "New" > "Python 3 Notebook".
2. Write and execute code in cells. Example:
```python
# Add two numbers
a = 5
b = 3
print("The sum is:", a + b)
```

---

## Part 2: Variables, Operators, Data Types, and Conditional Programming

### 1. Basics of Variables and Values

A variable is a container for storing data. Example:
```python
pizza_count = 4
pizza_type = "Margherita"
print(pizza_count, pizza_type)
```

#### Rules for Naming Variables:
1. Must start with a letter or underscore.
2. Cannot contain special characters like `@`, `$`.
3. Use underscores for multi-word names (e.g., `pizza_count`).

### 2. Operators in Python

#### Arithmetic Operators:
```python
a = 10
b = 3
print(a + b)  # Addition
print(a - b)  # Subtraction
print(a * b)  # Multiplication
print(a / b)  # Division
print(a // b)  # Floor Division
print(a % b)  # Modulus
print(a ** b)  # Exponentiation
```

#### Comparison Operators:
```python
print(a > b)  # Greater than
print(a < b)  # Less than
print(a == b)  # Equal to
```

#### Logical Operators:
```python
x = True
y = False
print(x and y)
print(x or y)
print(not x)
```

#### Assignment Operators:
```python
a += 5  # Same as a = a + 5
a *= 2  # Same as a = a * 2
```

#### Membership Operators:
```python
pizza_toppings = ["cheese", "pepperoni"]
print("cheese" in pizza_toppings)  # True
```

### 3. Core Data Types in Python

#### Integers and Floats:
```python
age = 25
price = 19.99
print(age + 5)
print(price * 2)
```

#### Strings:
```python
pizza = "Margherita"
print(pizza.upper())
print(pizza[:4])
```

#### Complex Numbers:
```python
z = 3 + 4j
print(z.real, z.imag)
```

#### Boolean:
```python
is_hungry = True
print(not is_hungry)
```

#### Lists:
```python
toppings = ["cheese", "pepperoni"]
toppings.append("mushrooms")
print(toppings)
```

#### Tuples:
```python
coordinates = (10, 20)
print(coordinates[0])
```

#### Dictionaries:
```python
pizza = {"type": "Margherita", "price": 8.5}
print(pizza["type"])
```

#### Sets:
```python
unique_toppings = {"cheese", "pepperoni"}
print(unique_toppings)
```

### 4. Conditional Programming

#### Basic If-Else:
```python
topping = "pineapple"
if topping == "pepperoni":
    print("Classic choice!")
else:
    print("Do we really want pineapple?")
```

#### Nested If Statements:
```python
size = "large"
extra_cheese = True
if size == "large":
    if extra_cheese:
        print("Large pizza with extra cheese!")
    else:
        print("Large pizza, no extra cheese.")
```

#### Logical Operators with Conditions:
```python
topping = "pepperoni"
extra = "olives"
if topping == "pepperoni" and extra == "olives":
    print("The perfect combo!")
```

---

### Detailed Explanations and Examples

#### 1. Introduction to Variables and Memory Management
Variables are names that store references to data in memory. Python automatically manages memory allocation for variables.

```python
x = 10
name = "Alice"
print(x)
print(name)
```

#### 2. Assigning and Updating Variables
Variables can be reassigned with new values.

```python
counter = 10
counter += 1
print(counter)  # 11
```

#### 3. Numeric Data Types: int, float, complex
Python supports various numeric data types:

- **int**: Integer values
- **float**: Decimal numbers
- **complex**: Numbers with a real and imaginary part

```python
integer_value = 42
float_value = 3.14
complex_value = 2 + 3j
print(integer_value, float_value, complex_value)
```

#### 4. Text Data Types: str
Strings are sequences of characters enclosed in quotes.

```python
text = "Hello, World!"
print(text.upper())
print(len(text))
```

#### 5. Boolean and NoneType
- **Boolean** values represent True or False.
- **NoneType** is used to represent the absence of a value.

```python
is_valid = False
value = None
print(is_valid, value)
```

#### 6. Type Conversion and Type Casting
Python allows converting data types.

```python
x = 5  # int
y = float(x)  # Convert to float
z = str(x)  # Convert to string
print(x, y, z)
```

#### 7. Conditional Statements
Python's conditional statements execute code based on conditions.

```python
number = 10
if number > 0:
    print("Positive number")
elif number == 0:
    print("Zero")
else:
    print("Negative number")
```
