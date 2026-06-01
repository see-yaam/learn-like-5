# ** Python Basic**

## ⚙️ Setup — Python + VS Code Install & Run

### Step 1: Install Python

- Download from: https://www.python.org/downloads/
- Don't forget to check the 'Add Python to PATH' box during installation. If you don't, Python won't work from the CMD.

### Step 2: Install VS Code

- Download from: https://code.visualstudio.com/
- After installing, open VS Code, go to Extensions (Ctrl+Shift+X), search for 'Python' by Microsoft, and click install.

### Step 3: Create Project folder

- Create a folder anywhere you like, for example, `my-python`.
- Open **VS Code** and go to **File → Open Folder** to open that folder.
- Create a **New File** and name it `hello.py`.

### Step 4: Run the Script

Just Click the “Run” button on VS Code or just open the terminal in VS Code: (**Ctrl + `** )

Then:

```bash
python hello.py
```

---

## 📌 Table of Contents

1. [What is Python and Why Does It Exist?](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#1-what-is-python-and-why-does-it-exist)
2. [Two Ways to Run Python](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#2-two-ways-to-run-python)
3. [Python as a Calculator](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#3-python-as-a-calculator)
4. [Variables — Storing Values with Names](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#4-variables--storing-values-with-names)
5. [Data Types — int, float, str, bool](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#5-data-types--int-float-str-bool)
6. [Operations with Different Types](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#6-operations-with-different-types)
7. [Practice Questions](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#7-practice-questions)
8. [Chapter Summary Table](https://github.com/see-yaam/learn-like-5/tree/main/Introduction%20to%20Python/Chapter-01%20(Python%20Basic)#8-chapter-summary-table)

---


## 1. What is Python and Why Does It Exist?

### The Concept

Think of Python as the ultimate all-rounder of the coding world. It’s a "general-purpose" language, which is just a fancy way of saying **it can do pretty much anything.** It doesn't get stuck doing just one job. Whether you want to build a website, make a game, automate boring tasks, or dive into cool stuff like Data Science and AI—Python handles it all easily. It’s basically your go-to tool for bringing any tech idea to life!

Why did it become so popular?

- **Open source,** free to use, forever
- **Readable,** code looks close to English, not math symbols
- **Packages,** other people write tools (packages), and you just plug them in

Think of Python like a **toolbox**. The base Python is the box itself. Packages are the tools inside — someone already built a hammer (visualization), a screwdriver (database connection), a drill (machine learning). You don't build the tools, you just use them.

> **Package = reusable code someone else wrote so you don't have to.**
> 

---

## 2. Two Ways to Run Python

### The Concept

There are two ways you can give Python instructions:

| Mode | What it is | When to use |
| --- | --- | --- |
| **Shell (IPython)** | Type one command → see result immediately | Quick experiments, testing small ideas |
| **Script (.py file)** | Write many commands → run all at once | Real projects, saving your work |

### How the Shell Works

You type something → Python reads it → Python runs it → shows you the result.

In your terminal type `py` and hit enter. Then → 

```
4 + 5
9
```

That's it. No extra steps.

### How a Script Works (the code)

A `.py` file is just a **text file with Python commands**, run from top to bottom — like reading a recipe step by step.

```python
# This is a Python script
print(4 + 5)   # Python runs this line, then moves to next
print(10 / 2)  # Then this line
```

**Important rule:** In scripts, Python won't show you anything unless you explicitly use `print()`.

```python
4 + 5        # Python calculates this but shows NOTHING
print(4 + 5) # Now Python shows: 9
```

---

## 3. Python as a Calculator

### The Concept

Python handles all basic math operations. These are called **arithmetic operators**.

| Operation | Symbol | Example | Result |
| --- | --- | --- | --- |
| Addition | `+` | `4 + 5` | `9` |
| Subtraction | `-` | `10 - 3` | `7` |
| Multiplication | `*` | `3 * 5` | `15` |
| Division | `/` | `10 / 2` | `5.0` |
| Integer Division | `//` | `10 // 3` | `3` |
| Remainder (Modulo) | `%` | `10 % 3` | `1` |
| Power | `**` | `2 ** 3` | `8` |
|  |  |  |  |

> Division `/` always gives a float (decimal). `10 / 2` gives `5.0`, not `5`.
> 
> 
> Use `//` if you want a whole number result.
> 

### Code

```python
# Basic arithmetic in Python

# Addition
print(4 + 5)      # Output: 9

# Subtraction
print(5 - 5)      # Output: 0

# Multiplication
print(3 * 5)      # Output: 15

# Division — always returns float
print(10 / 2)     # Output: 5.0

# Integer division — drops decimal part
print(10 // 3)    # Output: 3

# Modulo — gives remainder
print(10 % 3)     # Output: 1

# Power — 2 to the power of 3
print(2 ** 3)     # Output: 8
```

---

## 4. Variables — Storing Values with Names

### The Concept

A **variable** is a named container that holds a value.

Instead of writing `68.7` everywhere in your code, you write `weight = 68.7` once — and from then on, just use `weight`. Python will remember what's inside.

Why does this matter?

```
Without variables:
bmi = 68.7 / (1.79 * 1.79)   # If weight changes, you edit every single line

With variables:
weight = 68.7
height = 1.79
bmi = weight / (height ** 2)  # Change weight once → bmi updates automatically
```

This is called **reproducibility. Y**our code adjusts itself when the input changes.

### How Assignment Works

```
variable_name = value
```

The `=` sign in Python does NOT mean "equals". It means **"store this value into this name"**.

```python
x = 5      # Store 5 into x
x = 10     # Now x holds 10 (the old 5 is gone)
```

### Rules for Variable Names

- Can contain letters, numbers, underscores: `my_height`, `weight1`
- **Cannot** start with a number: ~~`1weight`~~ is invalid
- **Case-sensitive:** `Height` and `height` are two different variables
- No spaces: use `_` instead → `monthly_savings` not ~~`monthly savings`~~

### Code

```python
# Defining variables
height = 1.79       # stores the number 1.79 with the name "height"
weight = 68.7       # stores 68.7 with the name "weight"

# Using variables in calculations
bmi = weight / (height ** 2)   # height ** 2 means height × height

# Printing the result
print(bmi)          # Output: 21.44127836209856

# Changing a variable
weight = 75.0       # update weight
bmi = weight / (height ** 2)   # bmi recalculates automatically
print(bmi)          # Output: 23.41...
```

---

## 5. Data Types — int, float, str, bool

### The Concept

Every value in Python has a **type**. The type tells Python what kind of data this is and what operations make sense on it.

There are 4 basic types you need right now:

### Type 1: `int` — Integer (whole numbers)

```python
age = 21          # whole number, no decimal
students = 30
```

No decimal point. Positive, negative, or zero.

### Type 2: `float` — Floating Point (decimal numbers)

```python
height = 1.79     # has a decimal point
temperature = -3.5
pi = 3.14159
```

Any number with a `.` in it is a float. Even `5.0` is a float, not an int.

### Type 3: `str` — String (text)

```python
name = "Seyam"             # double quotes
greeting = 'Hello!'        # single quotes — both work
sentence = "I am 21"       # numbers inside quotes are still strings
```

**Key point:** `"21"` is a string (text that looks like a number). `21` is an int. They behave completely differently.

### Type 4: `bool` — Boolean (True or False)

```python
is_logged_in = True      # capital T
is_admin = False         # capital F
```

Only two possible values: `True` or `False`. Used for conditions, filters, decisions.

### Checking the Type

Use the built-in `type()` function:

```python
print(type(21))         # <class 'int'>
print(type(1.79))       # <class 'float'>
print(type("Hello"))    # <class 'str'>
print(type(True))       # <class 'bool'>
```

### Code — All 4 Types Together

```python
# int — whole number
age = 21
print(type(age))           # <class 'int'>

# float — decimal number
height = 1.79
print(type(height))        # <class 'float'>

# str — text (use quotes, single or double)
intro = "Hello! How are you?"
print(type(intro))         # <class 'str'>

# bool — only True or False (capital letters matter!)
is_good = True
print(type(is_good))       # <class 'bool'>

# Checking a calculated value's type
savings = 100
new_savings = 40
total = savings + new_savings
print(type(total))         # <class 'int'> — int + int = int
```

---

## 6. Operations with Different Types

### The Concept

Python's operators (like `+`) behave **differently depending on the data type**. Same symbol, different result.

This is one of the most important things to understand in Python — the **type controls the behavior**.

### `+` with Numbers → Addition

```python
100 + 40    # → 140   (math addition)
```

### `+` with Strings → Concatenation (joining)

```python
"Hello" + " World"    # → "Hello World"   (text pasting)
```

The `+` didn't add numbers. It **glued** two pieces of text together. This is called **string concatenation**.

### `*` with Numbers → Multiplication

```python
3 * 5    # → 15
```

### `*` with String and Number → Repetition

```python
"ha" * 3    # → "hahahaha"   (repeats the string 3 times)
```

### What Happens When You Mix Types?

```python
"100" + 40    # ❌ ERROR — can't add string and int
```

Python refuses. It doesn't guess what you meant. You have to convert explicitly:

```python
int("100") + 40    # ✅ → 140   (convert string to int first)
```

### Type Conversion (Casting)

| Function | What it does | Example |
| --- | --- | --- |
| `int(x)` | Converts to integer | `int("21")` → `21` |
| `float(x)` | Converts to float | `float("3.14")` → `3.14` |
| `str(x)` | Converts to string | `str(100)` → `"100"` |
| `bool(x)` | Converts to boolean | `bool(0)` → `False` |

### Code

```python
# Setup
savings = 100
new_savings = 40
intro = "Hello! How are you?"

# int + int = int (addition)
total_savings = savings + new_savings
print(total_savings)           # 140
print(type(total_savings))     # <class 'int'>

# str + str = str (concatenation — text gluing)
double_intro = intro + intro
print(double_intro)
# Output: Hello! How are you?Hello! How are you?

# str * int = str repeated
laugh = "ha" * 3
print(laugh)                   # hahaha

# Mixing types causes error — must convert first
# print("savings: " + savings)  # ❌ ERROR
print("savings: " + str(savings))  # ✅ Output: savings: 100

# Type conversion examples
print(int("50"))               # 50 (string to int)
print(float(5))                # 5.0 (int to float)
print(str(3.14))               # "3.14" (float to string)
print(bool(0))                 # False (0 is always False)
print(bool(1))                 # True (any non-zero is True)
```

---

## 7. Practice Questions

### 🟢 Easy

**Q1.** Create a variable named `year` containing your birth year. Then, print your age. This is year `2026` .
Answer: 

```python
year = 2003
age = 2026 - year
print(age)   # Output: 23
```

---

**Q2.** What will be the output of the code below:

```python
x = "5"
y = "3"
print(x + y)
```

Answer: 
Output: `53` , because `x`and `y` are both string types. The `+` operator is performing string concatenation, not mathematical addition.

---

**Q3.** Use `type()` to check what is the data type of the result of `True + True`?

Answer: 

```python
print(type(True + True))   # <class 'int'>
# True = 1, False = 0 in Python's number system
# True + True = 1 + 1 = 2
```

---

### 🟡 Medium

**Q4.** Your monthly expense is `5000`TK Write a script to:

- Store 5000 in `monthly_expense`.
- Store 12 in `months`.
- Calculate and print `yearly_expense`.
- Create a `currency` string variable assigned to "BDT".
- Print "Yearly expense: 60000 BDT" using only variables.

Answer:

```python
monthly_expense = 5000
months = 12
yearly_expense = monthly_expense * months
currency = "BDT"
print("Yearly expense: " + str(yearly_expense) + " " + currency)
```

---

**Q5.** Which one is the valid Python variable name?

```
a) 1st_score
b) first_score
c) First Score
d) first-score
e) _score1
```

Answer:

- `1st_score` ❌ — cannot start with a number
- `first_score` ✅ — valid
- `First Score` ❌ — spaces are not allowed
- `first-score` ❌ — hyphens are not allowed
- `_score1` ✅ — can start with an underscore

---

**Q6.** What's the difference between `5 / 2` and `5 // 2`? What will be the data type for both?

Answer:

- `5 / 2` → `2.5` (type: `float`) — always gives a decimal
- `5 // 2` → `2` (type: `int`) — cuts off the decimal part

---

### 🔴 Hard / Think Deeper

**Q7.** This code will give an error. Why? Fix it:

```python
score = 95
message = "Your score is: " + score
print(message)
```

Answer:

```python
# Error because: string + int = TypeError
# Fix:
score = 95
message = "Your score is: " + str(score)   # convert int into the string
print(message)   # Output: Your score is: 95
```

---

**Q8.** How does the `bool` type interact with numbers in Python? Execute the code below and explain the reasoning behind the output:

```python
print(True + True)
print(True + False)
print(False + False)
print(True * 5)
```

Answer:

```python
print(True + True)    # 2  → True=1, 1+1=2
print(True + False)   # 1  → 1+0=1
print(False + False)  # 0  → 0+0=0
print(True * 5)       # 5  → 1*5=5
# Python এ bool আসলে int এর subtype। True=1, False=0।
```

---

**Q9.** Write a script that introduces yourself. It should include:

- Name (string)
- Age (int)
- CGPA (float)
- Whether you are a CSE student or not (bool)

Print everything as a formatted sentence.

Answer:

```python
name = "Seyam"
age = 21
cgpa = 3.75
is_cse_student = True

print("Name: " + name)
print("Age: " + str(age))
print("CGPA: " + str(cgpa))
print("CSE Student: " + str(is_cse_student))
```

---

## 8. Chapter Summary Table

| Concept | What it is | Example | Key Rule |
| --- | --- | --- | --- |
| **Shell** | Type & run immediately | `>>> 4+5` → `9` | Good for experiments |
| **Script (.py)** | File with commands | `python file.py` | Use `print()` to see output |
| **Variable** | Named container for a value | `height = 1.79` | `=` means store, not equals |
| **int** | Whole number | `21`, `-5`, `0` | No decimal point |
| **float** | Decimal number | `3.14`, `1.79` | Has `.` in it |
| **str** | Text | `"Hello"`, `'Hi'` | Must use quotes |
| **bool** | True or False | `True`, `False` | Capital T/F, only 2 values |
| **type()** | Check the type of a value | `type(3.14)` → `float` | Built-in function |
| **`+` on str** | Joins text (concatenation) | `"a"+"b"` → `"ab"` | Not addition! |
| **`+` on int/float** | Math addition | `3+4` → `7` | Normal math |
| **Type mismatch** | Causes TypeError | `"hi" + 5` ❌ | Must convert first |
| **str()** | Converts to string | `str(100)` → `"100"` | For mixing str + number |
| **int()** | Converts to int | `int("21")` → `21` | Works if string is a number |

---

```
Python is a toolbox.
The language itself is the box.
Everything you store, calculate, or decide lives inside one of four containers:

┌─────────────────────────────────────────────────────────────┐
│                     THE FOUR DATA TYPES                     │
├──────────┬──────────────────────────────────────────────────┤
│  int     │  Whole numbers. No dot.                          │
│          │  age = 21,  score = 100,  year = 2025            │
├──────────┼──────────────────────────────────────────────────┤
│  float   │  Numbers with a decimal point.                   │
│          │  cgpa = 3.75,  height = 1.79,  pi = 3.14         │
├──────────┼──────────────────────────────────────────────────┤
│  str     │  Text. Always wrapped in quotes.                 │
│          │  name = "Arif",  city = "Dhaka"                  │
├──────────┼──────────────────────────────────────────────────┤
│  bool    │  Only two values, capital letters matter.        │
│          │  is_active = True,  is_admin = False             │
└──────────┴──────────────────────────────────────────────────┘

Variables are labels, not boxes.
    x = 5     →   you're sticking a label "x" onto the value 5
    x = 10    →   you moved the label to 10 — the old 5 is gone

The = sign does not mean "equal".
It means "point this name at this value."

Operators behave differently depending on type:
    3 + 4         →  7          (math addition)
    "3" + "4"     →  "34"       (text glued together)
    "ha" * 3      →  "hahaha"   (text repeated)
    "3" + 4       →  TypeError  (can't mix str and int)

When types clash → convert first:
    str(100)      →  "100"
    int("21")     →  21
    float("3.5")  →  3.5

Two ways to run Python:
    Shell   →  type one line, see result immediately  (for experiments)
    Script  →  write many lines, run all at once      (for real work)
    In scripts, nothing shows unless you use print().
```

---
