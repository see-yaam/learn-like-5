---

## Table of Contents

1. What is a Function?
2. Built-in Functions You Already Know
3. Arguments — How You Talk to a Function
4. Optional Arguments — Flexible Inputs
5. How to Find and Learn Functions
6. What are Methods?
7. String Methods
8. List Methods
9. Methods That Modify vs. Methods That Return
10. What are Packages?
11. Installing a Package
12. Importing a Package — Three Ways
13. Practice Questions
14. Chapter Summary Table

---

## 1. What is a Function?

### The Concept

You've already been using functions. `type()`, `print()`, `len()` . Those are all functions.

A **function** is a block of pre-written code that does a specific job. Someone wrote it once, packaged it up, and gave it a name. You just call the name and it works.

> A function is like a vending machine. You press a button (call the function), it does something internally, and gives you a result. You don't need to know how it works inside. Just what button to press and what comes out.
> 

### Why Functions Exist

Without functions, you'd have to rewrite the same logic over and over. With functions, you write it once (or use what someone already wrote) and reuse it forever.

```python
# Without a function — find the highest score manually
scores = [78, 91, 55, 88, 63, 97, 42]
highest = scores[0]
for s in scores:
    if s > highest:
        highest = s
# ... that's a lot of code just to find one value

# With a function — one line
highest = max(scores)   # Done. max() does all that work for you.
print(highest)          # Output: 97
```

---

## 2. Built-in Functions You Already Know

### The Concept

Python ships with a set of **built-in functions** that is ready to use, no installation needed. You've been using several already.

```python
scores = [78, 91, 55, 88, 63, 97, 42]

# max() — finds the largest value
print(max(scores))      # Output: 97

# min() — finds the smallest value
print(min(scores))      # Output: 42

# len() — counts the number of items
print(len(scores))      # Output: 7

# sum() — adds all values
print(sum(scores))      # Output: 514

# sorted() — returns a sorted copy of the list
print(sorted(scores))   # Output: [42, 55, 63, 78, 88, 91, 97]

# round() — rounds a number
cgpa = 3.8745
print(round(cgpa, 2))   # Output: 3.87

# type() — returns the type of a value
print(type(scores))     # Output: <class 'list'>
```

### Storing the Result

A function call produces a value. You can store that value in a variable and keep using it.

```python
scores = [78, 91, 55, 88, 63, 97, 42]

top_score = max(scores)
print("Best score: " + str(top_score))   # Output: Best score: 97

# You can also nest functions — pass the result of one into another
print(str(len(scores)) + " students gave the exam")
# Output: 7 students gave the exam
```

---

## 3. Arguments — How You Talk to a Function

### The Concept

When you call a function, you pass it information. These pieces of information are called **arguments** (or inputs or parameters).

```python
function_name(argument1, argument2)
```

The function receives your arguments, processes them internally, and returns a result.

```python
# round() takes two arguments: the number, and the decimal places
round(3.74159, 2)    # number=3.74159, ndigits=2 → returns 3.74
round(3.74159, 0)    # rounds to 0 decimal places → returns 4.0
round(3.74159)       # no second argument → rounds to nearest int → returns 4
```

Think of arguments like **form fields**. The function is a form. Each field expects specific input. Fill it in correctly and the form works.

---

## 4. Optional Arguments — Flexible Inputs

### The Concept

An **optional argument** is an input you pass into a function that **you don't strictly have to provide**. If you skip it, the function doesn't crash; it just uses a pre-decided, backup value called a **default value**.

You can check this using `help()`.

```python
help(round)
# Output:
# round(number, ndigits=None)
# The return value is an integer if ndigits is omitted or None.
```

The `=None` part tells you `ndigits` is optional. If you don't pass it, Python uses `None`, which means "round to the nearest integer."

```python
# required argument only
round(3.14159)       # → 3  (ndigits defaults to None = whole number)

# both arguments
round(3.14159, 3)    # → 3.142  (rounded to 3 decimal places)
```

### Another Example — `sorted()`

```python
help(sorted)
# sorted(iterable, /, *, key=None, reverse=False)
```

`reverse` is optional. Default is `False` (ascending). Pass `True` to flip it.

```python
scores = [78, 91, 55, 88, 63]

# Default — ascending order
print(sorted(scores))               # [55, 63, 78, 88, 91]

# With optional argument — descending order
print(sorted(scores, reverse=True)) # [91, 88, 78, 63, 55]
```

---

## 5. How to Find and Learn Functions

### The Concept

You don't need to memorize every function. The real skill is knowing **how to look them up**.

Three ways to learn about a function:

**1. `help()` in Python — built-in docs**

```python
help(max)
help(sorted)
help(len)
```

**2. `?` in IPython/Jupyter**

```python
?round
?sorted
```

**3. Google / Python docs**

Whenever you think "Python must have a function for this," it probably does. Search for it. The official Python docs list every built-in function.

> Rule of thumb: if the task is standard (sort, count, find max, calculate length), there's already a function for it. Don't write your own.
> 

---

## 6. What are Methods?

### The Concept

Every value in Python is an **object. A** string is an object, a list is an object, an integer is an object. And each object comes with its own built-in functions that are attached to it. These attached functions are called **methods**.

The difference between a function and a method:

```python
# Function — you pass the object to it
len(scores)       # scores goes inside the brackets

# Method — you call it ON the object using dot notation
scores.index(91)  # call index() on the scores object
```

> Think of methods like tools that belong to a specific machine. A blender has its own "blend" button. A toaster has its own "toast" button. You don't call blend() on a toaster.
> 

```python
object.method(arguments)
```

Different object types have different methods. A string's methods don't work on a list, and vice versa.

---

## 7. String Methods

### The Concept

Strings have a rich set of methods for manipulating text. Importantly, **strings are immutable** — calling a method on a string does NOT change the original. It returns a new string.

```python
username = "seyam_dev"

# .upper() — all uppercase. Returns new string, original unchanged.
print(username.upper())         # Output: SEYAM_DEV
print(username)                 # Output: seyam_dev  — still the same!

# .capitalize() — first letter uppercase
name = "arif hossain"
print(name.capitalize())        # Output: Arif hossain

# .replace(old, new) — swaps characters or substrings
email = "user@example.com"
print(email.replace("example", "gmail"))   # Output: user@gmail.com

# .count(substring) — how many times something appears
text = "banana"
print(text.count("a"))          # Output: 3

# .upper() and .lower() — change case
course = "Introduction To Python"
print(course.lower())           # Output: introduction to python

# .strip() — removes whitespace from both ends
raw = "   hello world   "
print(raw.strip())              # Output: hello world
```

---

## 8. List Methods

### The Concept

Lists have methods too — but unlike strings, **some list methods modify the list in place** (they change the actual list, no return value). Others return a new value.

```python
# .index(value) — returns the index of the first match
scores = [78, 91, 55, 88, 63, 91, 42]
print(scores.index(91))         # Output: 1  (first occurrence)

# .count(value) — how many times a value appears
print(scores.count(91))         # Output: 2  (appears twice)

# .append(value) — adds one item to the END of the list
scores.append(100)
print(scores)                   # [78, 91, 55, 88, 63, 91, 42, 100]

# .remove(value) — removes the FIRST occurrence of a value
scores.remove(91)               # removes first 91
print(scores)                   # [78, 55, 88, 63, 91, 42, 100]

# .reverse() — reverses the list in place
scores.reverse()
print(scores)                   # [100, 42, 91, 63, 88, 55, 78]

# .sort() — sorts the list in place (ascending by default)
scores.sort()
print(scores)                   # [42, 55, 63, 78, 88, 91, 100]
```

---

## 9. Methods That Modify vs. Methods That Return

### The Concept — Most Common Beginner Mistake

This is where many beginners get confused. Some methods **return a value** (you can store it in a variable). Others **modify the object directly** and return `None`.

```python
scores = [88, 42, 77, 95, 61]

# WRONG — trying to store the result of .sort()
sorted_scores = scores.sort()
print(sorted_scores)    # Output: None  ← .sort() returns nothing

# RIGHT — .sort() modifies scores in place
scores.sort()
print(scores)           # Output: [42, 61, 77, 88, 95]  ← scores is now sorted

# RIGHT — use sorted() (built-in function) if you want a new sorted list
scores = [88, 42, 77, 95, 61]
sorted_scores = sorted(scores)      # sorted() returns a new list
print(sorted_scores)    # Output: [42, 61, 77, 88, 95]
print(scores)           # Output: [88, 42, 77, 95, 61]  ← unchanged
```

> Rule: `list.sort()` modifies in place. `sorted(list)` returns a new list. Pick based on whether you want to keep the original.
> 

---

## 10. What are Packages?

### The Concept

Python's built-in functions cover the basics. But for data science, machine learning, graphics, networking you need way more power. That's where **packages** come in.

A package is a collection of Python scripts (called modules), each containing related functions, methods, and types that all are focused on solving a specific domain of problems.

> A package is like a specialized toolbox. Python gives you a basic multitool out of the box. But if you're doing electrical work, you bring in the electrician's toolbox (a package). If you're doing data analysis, you bring in the data scientist's toolbox.
> 

**Key packages you'll use in data science:**

| Package | What it does |
| --- | --- |
| `numpy` | Fast numerical computation, arrays |
| `pandas` | Data manipulation and analysis |
| `matplotlib` | Data visualization and charts |
| `scikit-learn` | Machine learning algorithms |
| `math` | Basic math functions (comes with Python) |

Not all packages come pre-installed. You have to install what you need.

---

## 11. Installing a Package

### The Concept

Python uses a tool called **pip** to install packages from the internet. Run these commands in your terminal, not in your Python script.

```bash
# Install a package
pip install numpy
pip install pandas
pip install matplotlib

# If you're using Python 3 explicitly
pip3 install numpy
```

Once installed, you never have to install it again on that system. You just import it in your script whenever you need it.

---

## 12. Importing a Package — Three Ways

### The Concept

Installing a package puts it on your computer. But your Python script doesn't automatically know about it. You have to **import** it at the top of your script.

There are three common ways to do this.

### Method 1 — Full import (recommended)

```python
import math

# Now access everything with the package name as prefix
print(math.pi)           # Output: 3.141592653589793
print(math.sqrt(144))    # Output: 12.0
print(math.floor(3.9))   # Output: 3
```

**Why this is preferred:** When you see `math.sqrt()`, it's immediately clear where `sqrt` comes from. No ambiguity.

### Method 2 — Import with alias (very common in data science)

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Access with the alias instead of full package name
scores = np.array([78, 91, 55, 88, 63])
print(np.mean(scores))    # Output: 75.0
```

`np`, `pd`, `plt` are standard community aliases. Everyone uses them this way. You'll see them in every tutorial, Stack Overflow answer, and textbook.

### Method 3 — Selective import

```python
from math import pi, sqrt, floor

# Now use the function directly — no prefix needed
radius = 7
area = pi * radius ** 2
print(area)              # Output: 153.93...
print(sqrt(256))         # Output: 16.0
```

**When to use this:** When you only need one or two specific things from a package and don't want the prefix clutter. The downside: if you import many things this way, it gets unclear which package each function came from.

### Comparison

```python
# All three do the same thing — calculate pi * r^2
import math
print(math.pi * 5 ** 2)           # Method 1: clear origin

import math as m
print(m.pi * 5 ** 2)              # Method 2: short alias

from math import pi
print(pi * 5 ** 2)                # Method 3: no prefix (less clear)
```

> Standard practice: use `import package` or `import package as alias`. Use `from package import x` only for specific cases.
> 

---

## 13. Practice Questions

### Easy

**Q1.** You have a list of temperatures recorded over a week:

```python
temps = [36.5, 38.1, 37.4, 36.8, 39.2, 37.0, 36.9]
```

Without writing any loops, use built-in functions to:

- Print the highest temperature
- Print the lowest temperature
- Print the number of readings
- Print the average (hint: `sum` and `len` together)

Answer:

```python
temps = [36.5, 38.1, 37.4, 36.8, 39.2, 37.0, 36.9]

print(max(temps))              # Output: 39.2
print(min(temps))              # Output: 36.5
print(len(temps))              # Output: 7
print(sum(temps) / len(temps)) # Output: 37.414...  (average)
```

---

**Q2.** What is the difference between calling `len("Dhaka")` and calling `"Dhaka".upper()`? Which is a function call and which is a method call?

Answer: 

- `len("Dhaka")` is a **function call** — you pass the string to `len()` as an argument.
- `"Dhaka".upper()` is a **method call** — you call `.upper()` directly ON the string object using dot notation.
Both produce a result, but the calling style is different.

---

**Q3.** What does the following code output? Think before running:

```python
city = "chittagong"
print(city.upper())
print(city)
```

Answer:

```
CHITTAGONG    ← .upper() returns a new uppercase string
chittagong    ← original city variable is unchanged (strings are immutable)
```

---

### Medium

**Q4.** You have this list:

```python
subjects = ["CSE", "Math", "Physics", "English", "CSE", "Math", "CSE"]
```

Use list methods (not loops) to:

- Find how many times "CSE" appears
- Find the index of the first "Math"
- Add "Chemistry" to the end
- Remove the first "Physics"
- Print the final list

Answer:

```python
subjects = ["CSE", "Math", "Physics", "English", "CSE", "Math", "CSE"]

print(subjects.count("CSE"))    # Output: 3
print(subjects.index("Math"))   # Output: 1
subjects.append("Chemistry")
subjects.remove("Physics")
print(subjects)
# Output: ['CSE', 'Math', 'English', 'CSE', 'Math', 'CSE', 'Chemistry']
```

---

**Q5.** Explain what happens here and why it's a common mistake:

```python
marks = [55, 90, 72, 38, 88]
result = marks.sort()
print(result)
print(marks)
```

How do you fix it if you want a sorted copy while keeping the original intact?

Answer:

```python
# marks.sort() sorts marks in place AND returns None.
# So result = None, and marks is now sorted.

# Output:
# None    ← result is None because .sort() returns nothing
# [38, 55, 72, 88, 90]  ← marks was sorted in place

# Fix — use sorted() to get a new sorted list, keep original:
marks = [55, 90, 72, 38, 88]
result = sorted(marks)
print(result)   # [38, 55, 72, 88, 90]
print(marks)    # [55, 90, 72, 38, 88]  — unchanged
```

---

**Q6.** You want to use the `sqrt()` function from the `math` package. Write three different import statements that would let you do this — each in a different style — and show how the actual function call would look for each.

Answer: 

```python
# Style 1 — full import
import math
math.sqrt(144)     # → 12.0

# Style 2 — alias
import math as m
m.sqrt(144)        # → 12.0

# Style 3 — selective
from math import sqrt
sqrt(144)          # → 12.0
```

---

### Hard / Think Deeper

**Q7.** What is the output? Explain why each line works or doesn't:

```python
course_code = "cse1111"

a = course_code.upper()
b = course_code.replace("cse", "CSE")
c = course_code.count("1")

print(a)
print(b)
print(c)
print(course_code)  # Has the original changed?
```

Answer:

```python
# Output:
# CSE1111      ← .upper() returns a new all-caps string
# CSE1111      ← .replace() swapped "cse" to "CSE"
# 4            ← "1" appears 4 times in "cse1111"
# cse1111      ← original unchanged! strings are immutable.
```

---

**Q8.** A student wrote this code and got confused by the output:

```python
scores = [85, 72, 91, 60, 78]
scores.append(95)
scores.append(55)
scores.sort()
print(len(scores))
print(scores[-1])
print(scores.index(91))
```

Without running it, predict every output and explain your reasoning for each line.

Answer:

```python
# After .append(95) and .append(55): scores = [85, 72, 91, 60, 78, 95, 55]
# After .sort(): scores = [55, 60, 72, 78, 85, 91, 95]

print(len(scores))        # Output: 7  — 5 original + 2 appended
print(scores[-1])         # Output: 95  — last item after sort = largest
print(scores.index(91))   # Output: 5  — 91 is at index 5 in sorted list
```

---

**Q9.** You're building a GPA report tool. Write a script that:

- Stores 5 course grades as a list of floats
- Uses built-in functions to find the highest, lowest, and average grade
- Rounds the average to 2 decimal places
- Prints a formatted summary like: `"High: 4.0 | Low: 2.5 | Avg: 3.42"`
- Uses at least one import from the `math` package

Answer:

```python
import math

grades = [3.8, 3.2, 4.0, 2.5, 3.7]

highest = max(grades)
lowest  = min(grades)

# Calculate the average and round it to 2 decimal places
avg     = round(sum(grades) / len(grades), 2) 

# Using math.floor just to demonstrate a math package function
floor_avg = math.floor(avg * 100) / 100   # same as round, shown for demo

print("High: " + str(highest) + " | Low: " + str(lowest) + " | Avg: " + str(avg))
# Output: High: 4.0 | Low: 2.5 | Avg: 3.44
```

---

## 14. Chapter Summary Table

| Concept | Syntax | Example | Notes |
| --- | --- | --- | --- |
| Function call | `function(args)` | `max(scores)` | Pass object to function |
| Store result | `var = function(args)` | `best = max(scores)` | Reuse the output |
| Method call | `object.method(args)` | `scores.index(91)` | Function attached to object |
| Get help | `help(func)` | `help(round)` | Shows arguments and docs |
| Optional arg | `func(x, opt=default)` | `round(3.14, 2)` | `ndigits` is optional |
| String method | immutable — returns new | `name.upper()` | Original unchanged |
| List method (return) | returns value | `scores.index(91)` | Doesn't change list |
| List method (modify) | changes list in place | `scores.append(99)` | Returns None |
| `sorted()` | returns new sorted list | `sorted(scores)` | Original unchanged |
| `.sort()` | sorts list in place | `scores.sort()` | Returns None |
| Import full | `import package` | `import math` | Access as `math.pi` |
| Import alias | `import package as x` | `import numpy as np` | Access as `np.array()` |
| Selective import | `from pkg import fn` | `from math import pi` | Access as just `pi` |
| pip install | terminal command | `pip install numpy` | Run once per machine |

---

```
Python has three levels of code you can use:

Level 1 — Built-in functions (always available, no import)
  max(), min(), len(), sum(), print(), type(), round(), sorted()

Level 2 — Methods (built into each object type)
  "hello".upper()      → str method
  [1,2,3].append(4)    → list method
  [1,2,3].index(2)     → list method

Level 3 — Packages (install once, import as needed)
  import math          → math.pi, math.sqrt()
  import numpy as np   → np.array(), np.mean()
  import pandas as pd  → pd.read_csv(), pd.DataFrame()

Key distinction:
  function(object)   →  you bring the object to the function
  object.method()    →  the function lives inside the object

Key trap:
  .sort() modifies the list and returns None
  sorted() returns a new sorted list
  Never store the result of .sort() — it's always None
```

---