# Python Cheatsheet

> Quick reference for Python based on [quickref.me/python](https://quickref.me/python)

---

## Getting Started

### Hello World
```python
print("Hello, World!")
```

### Comments
```python
# Single-line comment

"""
Multi-line
comment
"""
```

### Variables
```python
age = 18          # int
name = "John"     # str
price = 19.99     # float
is_active = True  # bool
x = None          # NoneType
```

### Type Checking & Casting
```python
type(42)        # <class 'int'>
isinstance(42, int)  # True

int("4")        # 4
float("3.14")   # 3.14
str(4)          # '4'
bool(0)         # False
list((1, 2))    # [1, 2]
```

---

## Data Types

| Type        | Example                  |
|-------------|--------------------------|
| `int`       | `x = 10`                 |
| `float`     | `x = 3.14`               |
| `complex`   | `x = 1 + 2j`             |
| `str`       | `x = "hello"`            |
| `bool`      | `x = True`               |
| `list`      | `x = [1, 2, 3]`          |
| `tuple`     | `x = (1, 2, 3)`          |
| `set`       | `x = {1, 2, 3}`          |
| `dict`      | `x = {"a": 1}`           |
| `NoneType`  | `x = None`               |

---

## Strings

### Basics
```python
s = "Hello, World!"

len(s)              # 13
s[0]                # 'H'
s[-1]               # '!'
s[1:5]              # 'ello'
s[::2]              # 'Hlo ol!'
```

### Methods
```python
s.upper()           # 'HELLO, WORLD!'
s.lower()           # 'hello, world!'
s.strip()           # remove leading/trailing whitespace
s.lstrip()          # remove leading whitespace
s.rstrip()          # remove trailing whitespace
s.replace("l", "r") # 'Herro, Worrd!'
s.split(", ")       # ['Hello', 'World!']
", ".join(["a","b"]) # 'a, b'
s.startswith("He")  # True
s.endswith("!")     # True
s.find("World")     # 7
s.count("l")        # 3
s.isdigit()         # False
s.isalpha()         # False
```

### Formatting
```python
name = "Alice"
age = 30

# f-string (Python 3.6+)
print(f"Name: {name}, Age: {age}")

# format()
print("Name: {}, Age: {}".format(name, age))

# % operator
print("Name: %s, Age: %d" % (name, age))

# Multi-line string
text = """
Line 1
Line 2
"""
```

---

## Numbers

```python
# Arithmetic
10 + 3   # 13
10 - 3   # 7
10 * 3   # 30
10 / 3   # 3.3333...  (float division)
10 // 3  # 3          (integer division)
10 % 3   # 1          (modulus)
10 ** 3  # 1000       (exponent)

# Math functions
import math

abs(-5)           # 5
round(3.7)        # 4
math.sqrt(16)     # 4.0
math.ceil(4.2)    # 5
math.floor(4.8)   # 4
math.pi           # 3.14159...
math.log(100, 10) # 2.0
```

---

## Lists

### Basics
```python
fruits = ["apple", "banana", "cherry"]

fruits[0]           # 'apple'
fruits[-1]          # 'cherry'
fruits[1:3]         # ['banana', 'cherry']
len(fruits)         # 3
```

### Methods
```python
fruits.append("date")        # add to end
fruits.insert(1, "blueberry") # insert at index
fruits.extend(["fig", "grape"]) # merge list
fruits.remove("banana")      # remove by value
fruits.pop()                 # remove & return last
fruits.pop(0)                # remove & return at index
fruits.sort()                # sort in place
fruits.sort(reverse=True)    # sort descending
fruits.reverse()             # reverse in place
fruits.index("cherry")       # find index
fruits.count("apple")        # count occurrences
fruits.copy()                # shallow copy
fruits.clear()               # empty the list
```

### Unpacking
```python
a, b, c = [1, 2, 3]
first, *rest = [1, 2, 3, 4]   # first=1, rest=[2,3,4]
*init, last = [1, 2, 3, 4]    # init=[1,2,3], last=4
```

---

## Tuples

```python
t = (1, 2, 3)

t[0]         # 1
len(t)       # 3
t.count(2)   # 1
t.index(3)   # 2

# Single-element tuple needs a trailing comma
single = (42,)

# Unpacking
x, y, z = t
```

---

## Dictionaries

### Basics
```python
person = {"name": "Alice", "age": 30}

person["name"]          # 'Alice'
person.get("age")       # 30
person.get("email", "") # '' (default if missing)
person["email"] = "a@example.com"  # add/update
del person["age"]       # delete key
```

### Methods
```python
person.keys()           # dict_keys([...])
person.values()         # dict_values([...])
person.items()          # dict_items([...])
person.update({"x": 1}) # merge/update
person.pop("name")      # remove & return value
person.copy()           # shallow copy
person.clear()          # empty the dict
"name" in person        # True
```

### Iteration
```python
for key in person:
    print(key)

for key, value in person.items():
    print(key, value)
```

---

## Sets

```python
s = {1, 2, 3}

s.add(4)
s.remove(2)       # raises KeyError if not found
s.discard(2)      # safe remove
s.pop()           # remove & return arbitrary element
len(s)            # 3
2 in s            # True

# Set operations
a = {1, 2, 3}
b = {2, 3, 4}

a | b             # union       {1, 2, 3, 4}
a & b             # intersection {2, 3}
a - b             # difference  {1}
a ^ b             # symmetric diff {1, 4}
a.issubset(b)     # False
a.issuperset(b)   # False
```

---

## Control Flow

### if / elif / else
```python
age = 20

if age < 13:
    print("Child")
elif age < 18:
    print("Teen")
else:
    print("Adult")

# Ternary / inline
status = "Adult" if age >= 18 else "Minor"
```

### for Loop
```python
for i in range(5):         # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 10, 2):  # 2, 4, 6, 8
    print(i)

for item in ["a", "b", "c"]:
    print(item)

for i, val in enumerate(["a", "b", "c"]):
    print(i, val)           # 0 a, 1 b, 2 c

for k, v in {"x": 1}.items():
    print(k, v)
```

### while Loop
```python
count = 0
while count < 5:
    print(count)
    count += 1
```

### Loop Control
```python
for i in range(10):
    if i == 3:
        continue    # skip to next iteration
    if i == 7:
        break       # exit loop
else:
    print("Loop completed")  # runs if no break
```

---

## Functions

### Basics
```python
def greet(name):
    return f"Hello, {name}!"

greet("Alice")   # 'Hello, Alice!'
```

### Default & Keyword Arguments
```python
def power(base, exp=2):
    return base ** exp

power(3)        # 9
power(3, 3)     # 27
power(exp=3, base=2)  # keyword args
```

### *args and **kwargs
```python
def add(*args):
    return sum(args)

add(1, 2, 3)    # 6

def info(**kwargs):
    for k, v in kwargs.items():
        print(k, v)

info(name="Alice", age=30)
```

### Lambda Functions
```python
square = lambda x: x ** 2
square(5)       # 25

add = lambda x, y: x + y
add(2, 3)       # 5

# Common uses
nums = [1, 2, 3, 4, 5]
list(map(lambda x: x**2, nums))       # [1, 4, 9, 16, 25]
list(filter(lambda x: x % 2 == 0, nums))  # [2, 4]
sorted([(1,2),(3,1)], key=lambda x: x[1]) # [(3,1),(1,2)]
```

---

## Comprehensions

### List Comprehension
```python
squares = [x**2 for x in range(10)]
evens = [x for x in range(10) if x % 2 == 0]
flat = [x for row in [[1,2],[3,4]] for x in row]
```

### Dict Comprehension
```python
d = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

### Set Comprehension
```python
consonants = {c for c in "hello" if c not in "aeiou"}
```

### Generator Expression
```python
gen = (x**2 for x in range(10))
next(gen)   # 0
sum(gen)    # 285
```

---

## Exception Handling

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
except (TypeError, ValueError) as e:
    print(f"Type or Value error: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
else:
    print("No exception occurred")
finally:
    print("Always runs")
```

### Raising Exceptions
```python
def check_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    return age
```

### Custom Exceptions
```python
class CustomError(Exception):
    def __init__(self, message):
        super().__init__(message)

raise CustomError("Something went wrong")
```

---

## Classes & OOP

### Basic Class
```python
class Person:
    species = "Homo sapiens"  # class attribute

    def __init__(self, name, age):
        self.name = name       # instance attribute
        self.age = age

    def greet(self):
        return f"Hi, I'm {self.name}"

    def __str__(self):
        return f"Person({self.name}, {self.age})"

    def __repr__(self):
        return f"Person(name={self.name!r}, age={self.age!r})"

p = Person("Alice", 30)
p.greet()        # "Hi, I'm Alice"
str(p)           # "Person(Alice, 30)"
```

### Inheritance
```python
class Student(Person):
    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self.grade = grade

    def greet(self):  # override
        return f"Hi, I'm {self.name}, grade {self.grade}"

s = Student("Bob", 20, "A")
isinstance(s, Person)    # True
issubclass(Student, Person)  # True
```

### Class & Static Methods
```python
class Circle:
    pi = 3.14159

    def __init__(self, radius):
        self.radius = radius

    def area(self):                     # instance method
        return Circle.pi * self.radius**2

    @classmethod
    def from_diameter(cls, diameter):   # class method
        return cls(diameter / 2)

    @staticmethod
    def is_valid_radius(r):             # static method
        return r > 0
```

### Properties
```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Too cold!")
        self._celsius = value

    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32
```

---

## Modules & Imports

```python
import math
import os
import sys
from datetime import datetime, timedelta
from collections import defaultdict, Counter
import json
import re

# Aliased import
import numpy as np
import pandas as pd

# Import all (avoid in large projects)
from math import *
```

---

## File I/O

### Reading Files
```python
# Read entire file
with open("file.txt", "r") as f:
    content = f.read()

# Read line by line
with open("file.txt", "r") as f:
    for line in f:
        print(line.strip())

# Read all lines into a list
with open("file.txt", "r") as f:
    lines = f.readlines()
```

### Writing Files
```python
# Write (overwrites existing)
with open("file.txt", "w") as f:
    f.write("Hello, World!\n")

# Append
with open("file.txt", "a") as f:
    f.write("New line\n")

# Write multiple lines
lines = ["line 1\n", "line 2\n"]
with open("file.txt", "w") as f:
    f.writelines(lines)
```

### File Modes
| Mode | Description            |
|------|------------------------|
| `r`  | Read (default)         |
| `w`  | Write (truncate)       |
| `a`  | Append                 |
| `x`  | Create (fails if exists)|
| `b`  | Binary mode            |
| `t`  | Text mode (default)    |

---

## Iterators & Generators

### Iterators
```python
my_list = [1, 2, 3]
it = iter(my_list)

next(it)    # 1
next(it)    # 2
next(it)    # 3
```

### Generators
```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for val in countdown(5):
    print(val)    # 5, 4, 3, 2, 1
```

---

## Useful Built-ins

```python
# Sequence helpers
len([1, 2, 3])          # 3
sum([1, 2, 3])          # 6
min([1, 2, 3])          # 1
max([1, 2, 3])          # 3
sorted([3, 1, 2])       # [1, 2, 3]
reversed([1, 2, 3])     # iterator
enumerate(["a","b"])    # (0,'a'), (1,'b')
zip([1,2], ["a","b"])   # (1,'a'), (2,'b')
map(str, [1, 2, 3])     # ['1','2','3']
filter(None, [0,1,2])   # [1, 2]
any([False, True])      # True
all([True, True])       # True

# Object info
dir(list)               # list all attributes
help(str)               # show documentation
id(obj)                 # memory address
hash(42)                # hash value
```

---

## Regular Expressions

```python
import re

text = "Phone: 123-456-7890"

re.search(r"\d{3}-\d{3}-\d{4}", text)    # match object
re.findall(r"\d+", text)                  # ['123', '456', '7890']
re.sub(r"\d", "*", text)                  # 'Phone: ***-***-****'
re.split(r"\s+", "hello world")           # ['hello', 'world']
re.match(r"Phone", text)                  # match at start

# Compile pattern for reuse
pattern = re.compile(r"\d{3}-\d{3}-\d{4}")
pattern.search(text)
```

---

## Useful Standard Library Modules

```python
import os
os.getcwd()                 # current directory
os.listdir(".")             # list files
os.path.join("a", "b")     # path joining
os.path.exists("file.txt")  # check existence
os.makedirs("dir", exist_ok=True)  # create dir

import sys
sys.argv                    # command-line arguments
sys.exit(0)                 # exit program

import json
json.dumps({"a": 1})        # '{"a": 1}'
json.loads('{"a": 1}')      # {"a": 1}
with open("f.json") as f:
    data = json.load(f)

from datetime import datetime
datetime.now()
datetime.now().strftime("%Y-%m-%d %H:%M:%S")

from collections import Counter, defaultdict, deque
Counter("hello")            # {'l': 2, 'h': 1, 'e': 1, 'o': 1}
defaultdict(int)            # dict with default int value
deque([1,2,3])              # double-ended queue
```

---

## Virtual Environments & pip

```bash
# Create virtual environment
python -m venv venv

# Activate
source venv/bin/activate       # macOS/Linux
venv\Scripts\activate          # Windows

# Deactivate
deactivate

# Install packages
pip install requests
pip install -r requirements.txt

# Freeze dependencies
pip freeze > requirements.txt
```

---

*Reference: [quickref.me/python](https://quickref.me/python)*
