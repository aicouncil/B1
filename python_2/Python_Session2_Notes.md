# Python Programming Concepts with Definitions and Examples

## Conditional Programming: Simulating Login Activity

### Definition:
Conditional programming involves using statements like `if`, `else`, and `elif` to control the flow of a program based on certain conditions.

### Example 1: Simple Login Simulation
```python
uid = input("Enter Your user ID")
upass = input("Enter Your password")

if uid == 'admin' and upass == 'password':
    print("Login successful")
else:
    print('Incorrect Login credentials')
```
**Explanation:**
- The program takes a user ID and password as inputs.
- If both match the predefined values, it prints "Login successful."
- Otherwise, it prints "Incorrect Login credentials."

### Example 2: Nested If Login Simulation
```python
uid = input("Enter Your user ID")

if uid == 'admin':
    upass = input("Enter Your password")
    if upass == 'password':
        print('Login Successful')
    else:
        print('Incorrect password')
else:
    print("Invalid user")
```
**Explanation:**
- Only asks for a password if the user ID is correct.
- Checks both conditions (user ID and password) using nested `if` statements.

---

## Loops: For and While

### Definition:
Loops are used to execute a block of code repeatedly until a specific condition is met. Common types include `for` and `while` loops.

### For Loop Examples

#### Repeated Output
```python
for i in range(5):
    print("Hello World!")
```
**Explanation:**
- `range(5)` generates numbers from 0 to 4.
- The loop prints "Hello World!" five times.

#### Breaking a Loop
```python
for i in range(10):
    print(i, "Hello World!")
    if i == 7:
        break
```
**Explanation:**
- The loop terminates early when `i` equals 7.

#### Skipping Iterations
```python
for i in range(10):
    if i == 7:
        continue
    print(i, "Hello World!")
```
**Explanation:**
- The `continue` statement skips the iteration when `i` equals 7.

#### Implementing Step Size
```python
for i in range(0, 10, 2):
    print(i)
```
**Explanation:**
- The loop increments `i` by 2, printing every second number from 0 to 8.

#### Iterating Over a List
```python
cities = ['Chennai', 'Hyderabad', 'Mumbai']
for city in cities:
    print(city, len(city))
```
**Explanation:**
- Iterates through a list of cities and prints each city along with its length.

### While Loop Examples

#### Basic While Loop
```python
i = 0
while i < 5:
    print("Hello World")
    i += 1
```
**Explanation:**
- Prints "Hello World" while `i` is less than 5.
- Increments `i` by 1 in each iteration.

#### Simulating Login
```python
while True:
    uid = input("Enter Your user ID")
    upass = input("Enter Your password")

    if uid == 'admin' and upass == 'password':
        print("Login successful")
        break
    else:
        print('Incorrect Login credentials')
```
**Explanation:**
- Continuously asks for login credentials until they are correct.

---

## Functions

### Definition:
Functions are reusable blocks of code that perform a specific task. They can accept inputs (parameters) and return outputs.

### Creating and Using Functions

#### Example 1: Addition Function
```python
def add_nums(x, y):
    return x + y

result = add_nums(7, 9)
print(result)
```
**Explanation:**
- `add_nums` is a function that adds two numbers and returns the result.
- The result is printed after calling the function.

#### Example 2: Check Even or Odd
```python
def even_or_odd(x):
    if x % 2 == 0:
        print(x, "is even")
    else:
        print(x, "is odd")

even_or_odd(7)
even_or_odd(72)
```
**Explanation:**
- The function checks if a number is divisible by 2.
- Prints whether the number is "even" or "odd."

#### Example 3: Voting Eligibility
```python
def voting(name, age):
    if age >= 18:
        print("Hello", name, ",You have the voting right")
    else:
        print("Hello", name, ",You don't have the voting right")

voting("Raj", 22)
voting("Ajay", 17)
```
**Explanation:**
- The function checks if the age is 18 or above and prints a corresponding message.

### Return Type Functions

#### Example 1: Login Check
```python
def login(uid, upass):
    if uid == 'admin' and upass == 'password':
        return True
    else:
        return False

user_id = input("Enter User id")
user_pass = input("Enter your password")

if login(user_id, user_pass):
    print("Your login is successful")
else:
    print("Your login is not successful")
```
**Explanation:**
- The function returns `True` for correct credentials and `False` otherwise.

#### Example 2: Find Largest Number
```python
def compare(x, y=1):
    return x if x > y else y

result = compare(6, 3)
print("The largest number is", result)
```
**Explanation:**
- Compares two numbers and returns the larger one.
- Uses a default value for `y` if not provided.

#### Example 3: Add Multiple Numbers
```python
def add_numbers(x=0, y=0, z=0):
    return x + y + z

print(add_numbers(6, 3, 4))
```
**Explanation:**
- Adds up to three numbers with default values of 0.

---

### Downloadable Markdown
This content is available for download as a markdown file.
