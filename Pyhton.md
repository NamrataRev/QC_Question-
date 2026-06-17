# Python Interview Questions & Answers

---

# Core Python

## Why do we call Python a dynamically typed language?

Python is dynamically typed because the type of a variable is determined at runtime, not during compilation.

```python
x = 10      # int
x = "Hello" # str
```

The same variable can hold different data types during execution.

---

## What are Flow Control Statements in Python?

Flow control statements control the execution order of statements.

### break

Terminates the loop immediately.

```python
for i in range(5):
    if i == 3:
        break
    print(i)
```

Output:

```text
0
1
2
```

### continue

Skips the current iteration and moves to the next iteration.

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

Output:

```text
0
1
3
4
```

---

## Talk about Strings in Python. How do you create a multiline string?

Strings are sequences of characters enclosed within single, double, or triple quotes.

### Multiline String

```python
text = """This is
a multiline
string"""
```

or

```python
text = '''This is
a multiline
string'''
```

---

## Difference Between List, Tuple, and Set

| Feature | List | Tuple | Set |
|----------|---------|---------|---------|
| Ordered | Yes | Yes | No |
| Mutable | Yes | No | Yes |
| Duplicates | Allowed | Allowed | Not Allowed |
| Syntax | [] | () | {} |

### Examples

```python
my_list = [1, 2, 3]
my_tuple = (1, 2, 3)
my_set = {1, 2, 3}
```

---

## When Will You Choose List, Tuple, Set, and Dictionary?

### List

Use when:

- Order matters
- Data needs modification

```python
employees = ["John", "Mike"]
```

### Tuple

Use when:

- Data should not change
- Faster than lists

```python
coordinates = (10, 20)
```

### Set

Use when:

- Need unique values
- Fast membership testing

```python
skills = {"Python", "Java"}
```

### Dictionary

Use when:

- Need key-value pairs

```python
employee = {
    "id": 101,
    "name": "John"
}
```

---

# OOP

## What is a Constructor in Python?

A constructor initializes object attributes.

```python
class Employee:
    def __init__(self, name):
        self.name = name
```

```python
emp = Employee("John")
```

---

## Purpose of super()

Used to access parent class methods and constructor.

```python
class Parent:
    def __init__(self):
        print("Parent Constructor")

class Child(Parent):
    def __init__(self):
        super().__init__()
        print("Child Constructor")
```

Output:

```text
Parent Constructor
Child Constructor
```

### What happens if super() is called inside __init__()?

Parent constructor executes before child constructor logic.

---

## What is Polymorphism?

Same interface, different implementations.

### Types

1. Method Overriding
2. Operator Overloading
3. Duck Typing

### Method Overriding

```python
class Animal:
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        print("Bark")
```

---

## Does Python Support Method Overloading?

No, Python does not support traditional method overloading.

### Example

```python
class Demo:
    def add(self, a):
        pass

    def add(self, a, b):
        pass
```

Only the latest method definition survives.

### Achieving Overloading

Using default arguments:

```python
def add(a, b=0):
    return a + b
```

Using *args:

```python
def add(*args):
    return sum(args)
```

---

## How Do We Achieve Encapsulation?

Using private and protected members.

### Protected

```python
class Employee:
    _salary = 50000
```

### Private

```python
class Employee:
    __salary = 50000
```

### Difference

| Protected | Private |
|------------|----------|
| _var | __var |
| Convention only | Name mangling |
| Accessible in subclass | Not directly accessible |

---

## How Do We Achieve Abstraction?

Using Abstract Base Classes (ABC).

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):

    @abstractmethod
    def start(self):
        pass
```

---

# Exception Handling

## What are Exceptions?

Exceptions are runtime errors that interrupt program execution.

### Handling Exceptions

```python
try:
    num = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

---

## When Will You Use finally Block?

Used for cleanup operations.

Example:

```python
file = open("data.txt")

try:
    data = file.read()
finally:
    file.close()
```

The finally block executes whether an exception occurs or not.

---

## How Can You Throw an Exception Explicitly?

```python
raise ValueError("Invalid value")
```

---

## Create a Custom Exception

```python
class AgeException(Exception):
    pass

age = -1

if age < 0:
    raise AgeException("Age cannot be negative")
```

---

## Purpose of with Statement

Automatically manages resources.

```python
with open("data.txt") as file:
    content = file.read()
```

Automatically closes the file.

---

# File Handling

## Methods to Read Files

### read()

Reads entire file.

```python
file.read()
```

### readline()

Reads one line.

```python
file.readline()
```

### readlines()

Reads all lines into a list.

```python
file.readlines()
```

---

## File Open Modes

| Mode | Description |
|--------|-------------|
| r | Read |
| w | Write |
| a | Append |
| x | Create |
| rb | Read Binary |
| wb | Write Binary |
| r+ | Read & Write |

Example:

```python
open("data.txt", "r")
```

---

## Rename or Delete a File

```python
import os

os.rename("old.txt", "new.txt")
```

```python
os.remove("new.txt")
```

---

# PIP

## Why Do We Use PIP?

PIP is Python's package manager.

Used to:

- Install packages
- Upgrade packages
- Remove packages

---

## Install Package

```bash
pip install pandas
```

## Upgrade Package

```bash
pip install --upgrade pandas
```

## Uninstall Package

```bash
pip uninstall pandas
```

---

# JSON

## Convert Python Dictionary to JSON String

```python
import json

data = {"name": "John"}

json_str = json.dumps(data)
```

---

## Convert JSON to Dictionary

```python
import json

json_str = '{"name":"John"}'

data = json.loads(json_str)
```

---

# Regular Expressions (re)

## Count Occurrences of Word "python"

```python
import re

text = "python is good. python is easy."

count = len(re.findall(r'python', text))
print(count)
```

Output:

```text
2
```

---

## Remove Extra Spaces

```python
import re

text = "Hello     World     Python"

result = re.sub(r'\s+', ' ', text)

print(result)
```

Output:

```text
Hello World Python
```

---

## Difference Between match(), search(), and findall()

### match()

Searches only at the beginning.

```python
re.match("python", text)
```

### search()

Searches first occurrence anywhere.

```python
re.search("python", text)
```

### findall()

Returns all matches.

```python
re.findall("python", text)
```

---

# Logging

## Logging Levels

| Level | Value |
|---------|--------|
| DEBUG | 10 |
| INFO | 20 |
| WARNING | 30 |
| ERROR | 40 |
| CRITICAL | 50 |

---

## Log Messages to a File

```python
import logging

logging.basicConfig(
    filename="app.log",
    level=logging.INFO
)

logging.info("Application Started")
```

---

# Iterator

## What is an Iterator?

An iterator is an object that allows traversing data one element at a time.

---

## Difference Between Iterable and Iterator

| Iterable | Iterator |
|-----------|-----------|
| Collection of items | Produces next item |
| Uses iter() | Uses next() |
| Example: list, tuple | Example: iterator object |

---

## Methods Required by an Iterator

### __iter__()

Returns iterator object.

### __next__()

Returns next value.

```python
class Counter:

    def __iter__(self):
        return self

    def __next__(self):
        pass
```

---

## Output of the Following Code

```python
nums = [1, 2, 3]

it1 = iter(nums)
it2 = iter(nums)

print(next(it1))
print(next(it1))
print(next(it2))
```

### Output

```text
1
2
1
```

### Explanation

- it1 and it2 are independent iterators.
- it1 moves twice.
- it2 starts from the beginning.

---

# Pandas

## Difference Between Series and DataFrame

| Series | DataFrame |
|----------|------------|
| One-dimensional | Two-dimensional |
| Single column | Multiple columns |

```python
import pandas as pd

s = pd.Series([1,2,3])
```

```python
df = pd.DataFrame({
    "id":[1,2]
})
```

---

## Two Ways to Create a DataFrame

### Method 1

```python
import pandas as pd

df = pd.DataFrame({
    "name":["John","Mike"],
    "age":[25,30]
})
```

### Method 2

```python
data = [
    ["John",25],
    ["Mike",30]
]

df = pd.DataFrame(
    data,
    columns=["name","age"]
)
```

---

## Create DataFrame from Dictionary

```python
import pandas as pd

data = {
    "name":["John","Mike"],
    "age":[25,30]
}

df = pd.DataFrame(data)
```

---

## Read CSV File

```python
import pandas as pd

df = pd.read_csv("employees.csv")
```

---

## Handle Missing Values

### Check Missing Values

```python
df.isnull()
```

### Remove Missing Values

```python
df.dropna()
```

### Fill Missing Values

```python
df.fillna(0)
```

---

# List Comprehension

```python
squares = [x*x for x in range(5)]
```

Output:

```python
[0,1,4,9,16]
```

With Condition:

```python
evens = [x for x in range(10) if x % 2 == 0]
```

---

# Lambda Function

Anonymous function.

```python
square = lambda x: x*x

print(square(5))
```

Output:

```text
25
```

---

# Map Function

Applies a function to every element.

```python
nums = [1,2,3,4]

result = list(map(lambda x:x*2, nums))

print(result)
```

Output:

```text
[2,4,6,8]
```

---

# Decorator

A decorator modifies the behavior of a function without changing its code.

```python
def logger(func):

    def wrapper():
        print("Before Function")
        func()
        print("After Function")

    return wrapper


@logger
def greet():
    print("Hello")


greet()
```

Output:

```text
Before Function
Hello
After Function
```

---