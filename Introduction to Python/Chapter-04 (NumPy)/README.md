---

# **4. NumPy**

## Table of Contents

1. Why NumPy Exists — The Problem with Lists
2. Creating a NumPy Array
3. Element-wise Calculations
4. NumPy Rule 1 — Single Type Only
5. NumPy Rule 2 — Operators Behave Differently
6. Subsetting NumPy Arrays — By Index
7. Boolean Subsetting — Filter with a Condition
8. 2D NumPy Arrays — From Lists of Lists
9. The .shape Attribute
10. Subsetting 2D Arrays
11. Slicing 2D Arrays — Rows and Columns
12. Element-wise Arithmetic on 2D Arrays
13. NumPy Basic Statistics
14. Mean vs Median — When Each Matters
15. Practice Questions
16. Chapter Summary Table

---

## 1. Why NumPy Exists — The Problem with Lists

### The Concept

Python lists are flexible and they can hold any type, you can add and remove items. But they have one major weakness for data science that **you cannot do math on an entire list at once.**

Imagine you have the scores of 500 students, and you want to add 5 bonus marks to every score. With a regular list, Python has no idea how to do that in one shot.

```python
scores = [72, 85, 91, 60, 78]

# Try to add 5 to every score at once
scores + 5
# TypeError: can only concatenate list (not "int") to list
# Python refuses. It doesn't know how to add a number to a whole list.

# You'd have to do it one by one that is slow for large data
```

### The Solution — NumPy

NumPy (Numeric Python) gives you a new data structure called the **NumPy array**. It looks like a list, acts like a list for many things, but supports math operations across the entire array at once — fast.

```bash
# Install once in your terminal
pip install numpy
```

---

## 2. Creating a NumPy Array

### The Concept

You always start from a regular Python list. Pass it into `np.array()` and you get a NumPy array back. Same values, different type — with superpowers.

> However, NumPy is a package. To know more about packages and how to import click here.
> 

```python
import numpy as np

# Start with a regular list
scores = [72, 85, 91, 60, 78]

# Convert to a NumPy array
np_scores = np.array(scores)

print(np_scores)
# Output: array([72 85 91 60 78])

print(type(np_scores))
# Output: <class 'numpy.ndarray'>
# ndarray = n-dimensional array
```

You can also create a NumPy array directly:

```python
import numpy as np

# Directly from a list literal
cgpa_list = [3.75, 3.50, 3.92, 3.67, 3.80]
np_cgpa = np.array(cgpa_list)

print(np_cgpa)
# Output: [3.75 3.5  3.92 3.67 3.8 ]
```

> Notice: NumPy arrays print without commas between values. That's how you can tell them apart from regular lists visually.
> 

---

## 3. Element-wise Calculations

### The Concept

This is the entire reason NumPy exists. When you apply a math operation to a NumPy array, it applies that operation to **every element individually** — automatically, all at once.

This is called **element-wise operation**.

```python
import numpy as np

scores     = np.array([72, 85, 91, 60, 78])
bonus      = 5

# Add 5 to every score — element-wise
new_scores = scores + bonus
print(new_scores)
# Output: [77 90 96 65 83]  ← every score got +5

# Multiply every score by 2
double = scores * 2
print(double)
# Output: [144 170 182 120 156]
```

### Real Example — CGPA from raw marks

```python
import numpy as np

raw_marks  = np.array([380, 350, 420, 310, 395])  # out of 500
total      = 500
cgpa_scale = 4.0

# Convert to CGPA scale in one line — element-wise division then multiply
cgpa = (raw_marks / total) * cgpa_scale

print(cgpa)
# Output: [3.04 2.8  3.36 2.48 3.16]
```

### Operations between two arrays

```python
import numpy as np

mid_marks   = np.array([35, 40, 28, 45, 38])   # out of 50
final_marks = np.array([55, 62, 48, 70, 60])   # out of 100

# Add corresponding elements
total = mid_marks + final_marks
print(total)
# Output: [90 102  76 115  98]
# 35+55=90, 40+62=102, 28+48=76 ... each pair adds up
```

> The arrays must have the same length for element-wise operations between two arrays. Otherwise NumPy throws an error.
> 

---

## 4. NumPy Rule 1 — Single Type Only

### The Concept

A regular Python list can hold any mix of types: `[1, "hello", True, 3.14]`. That's fine.

A NumPy array **enforces a single data type**. Every element must be the same type. This is what makes NumPy fast — a uniform block of memory is much faster to compute on than a scattered mix.

If you try to create a NumPy array with mixed types, NumPy doesn't throw an error. Instead, it **silently converts everything** to the most flexible type that can hold all values and usually a string.

```python
import numpy as np

# Mixed types — float, string, bool
mixed = np.array([3.14, "hello", True])
print(mixed)
# Output: ['3.14' 'hello' 'True']
# Everything became a string. Python didn't warn you. It just converted.

print(mixed.dtype)
# Output: <U32  (Unicode string with max 32 characters)
```

```python
import numpy as np

# Bool and int mixed — bool becomes int (True=1, False=0)
mixed2 = np.array([True, False, 1, 2, 3])
print(mixed2)
# Output: [1 0 1 2 3]  ← True became 1, False became 0

print(mixed2.dtype)
# Output: int64
```

> **Rule:** When you create a NumPy array, always make sure all values are the same type. Otherwise you'll get unexpected silent conversions that will break your calculations later.
> 

---

## 5. NumPy Rule 2 — Operators Behave Differently

### The Concept

The `+` operator means different things for lists vs NumPy arrays. This trips up beginners constantly.

```python
import numpy as np

python_list  = [10, 20, 30]
numpy_array  = np.array([10, 20, 30])

# + on two lists = concatenation (gluing)
print(python_list + python_list)
# Output: [10, 20, 30, 10, 20, 30]   ← 6 elements, pasted together

# + on two NumPy arrays = element-wise addition
print(numpy_array + numpy_array)
# Output: [20 40 60]   ← 10+10, 20+20, 30+30
```

Same symbol, completely different behavior depending on type.

```python
import numpy as np

# More examples
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)    # [5 7 9]
print(a * b)    # [4 10 18]
print(a - b)    # [-3 -3 -3]
print(b / a)    # [4.  2.5  2. ]
print(a ** 2)   # [1 4 9]   ← square each element
```

---

## 6. Subsetting NumPy Arrays — By Index

### The Concept

Subsetting works exactly the same as Python lists — square brackets with an index. The rules are the same: starts at 0, negative indexes count from the end, slicing with `[start:end]`.

```python
import numpy as np

np_scores = np.array([72, 85, 91, 60, 78, 95, 55, 88])
#  index:              0   1   2   3   4   5   6   7
#  neg:               -8  -7  -6  -5  -4  -3  -2  -1

# Single element
print(np_scores[0])    # Output: 72   (first element)
print(np_scores[2])    # Output: 91   (third element)
print(np_scores[-1])   # Output: 88   (last element)

# Slice — elements at index 1 to 4 (index 5 not included)
print(np_scores[1:5])  # Output: [85 91 60 78]

# From index 4 to end
print(np_scores[4:])   # Output: [78 95 55 88]

# First 3 elements
print(np_scores[:3])   # Output: [72 85 91]
```

---

## 7. Boolean Subsetting — Filter with a Condition

### The Concept

This is something you **cannot** do with regular Python lists. NumPy lets you use a condition to filter an array — and it's one of the most powerful tools in data science.

**Step 1:** Compare the array to a value. This returns an array of `True`/`False` values.

**Step 2:** Use that boolean array to select only the elements where the condition is `True`.

```python
import numpy as np

np_scores = np.array([72, 85, 91, 60, 78, 95, 55, 88])

# Step 1 — which scores are above 80?
above_80 = np_scores > 80
print(above_80)
# Output: [False  True  True False False  True False  True]
#            72    85    91    60    78    95    55    88
# True where score > 80, False everywhere else

# Step 2 — use the boolean array to select those scores
print(np_scores[above_80])
# Output: [85 91 95 88]
```

You can do it in one line:

```python
import numpy as np

np_scores = np.array([72, 85, 91, 60, 78, 95, 55, 88])

# One-liner — filter directly
print(np_scores[np_scores > 80])
# Output: [85 91 95 88]

# Other conditions work the same way
print(np_scores[np_scores == 60])   # Output: [60]      (exact match)
print(np_scores[np_scores < 70])    # Output: [60 55]   (below 70)
print(np_scores[np_scores >= 90])   # Output: [91 95]   (90 or above)
```

> Think of boolean subsetting as a filter mask. The `True` cells let light through. The `False` cells block it. Only the values under `True` make it through.
> 

---

## 8. 2D NumPy Arrays — From Lists of Lists

### The Concept

So far all arrays were 1D that was a single row of values. But real data is usually a **table**: multiple rows and columns. This is where 2D NumPy arrays come in.

A 2D array is created from a **list of lists**. Each inner list becomes one row of the table.

```python
import numpy as np

# 5 students, each with [cgpa, attendance_percentage]
student_data = [
    [3.75, 88],
    [3.50, 72],
    [3.92, 95],
    [3.67, 80],
    [3.80, 91]
]

np_students = np.array(student_data)
print(np_students)
# Output:
# [[ 3.75 88.  ]
#  [ 3.5  72.  ]
#  [ 3.92 95.  ]
#  [ 3.67 80.  ]
#  [ 3.8  91.  ]]

print(type(np_students))
# Output: <class 'numpy.ndarray'>
```

---

## 9. The .shape Attribute

### The Concept

`shape` is an **attribute** of a NumPy array that tells you its dimensions: how many rows and how many columns.

Note: `shape` is NOT a method. Methods have parentheses `()`. Attributes don't. Learn more from methods from here.

```python
import numpy as np

student_data = [[3.75, 88], [3.50, 72], [3.92, 95], [3.67, 80], [3.80, 91]]
np_students = np.array(student_data)

print(np_students.shape)
# Output: (5, 2)
# 5 rows (students), 2 columns (cgpa, attendance)

# 1D array shape
np_scores = np.array([72, 85, 91, 60, 78])
print(np_scores.shape)
# Output: (5,)  — 5 elements, 1 dimension
```

---

## 10. Subsetting 2D Arrays

### The Concept

For 2D arrays, you need **two indexes**: one for the row, one for the column.

```
array[row_index, column_index]
```

The comma-based syntax is the standard NumPy way. You can also use two sets of square brackets, but the comma style is preferred.

```python
import numpy as np

# Rows = students, Columns = [cgpa, attendance]
np_students = np.array([
    [3.75, 88],   # row 0
    [3.50, 72],   # row 1
    [3.92, 95],   # row 2
    [3.67, 80],   # row 3
    [3.80, 91]    # row 4
])
#  columns:   0     1

# Get the entire first row (student 0)
print(np_students[0])
# Output: [3.75 88.]

# Get a specific value — row 2, column 0 (student 2's cgpa)
print(np_students[2, 0])    # Output: 3.92

# Same thing with two brackets (older style, less preferred)
print(np_students[2][0])    # Output: 3.92

# Get row 3, column 1 (student 3's attendance)
print(np_students[3, 1])    # Output: 80.0
```

---

## 11. Slicing 2D Arrays — Rows and Columns

### The Concept

The real power of 2D arrays is selecting **entire rows or columns**, or rectangular slices of the table.

The syntax is:

```python
array[row_selection, column_selection]
```

Use `:` to mean "all" — all rows or all columns.

```python
import numpy as np

np_students = np.array([
    [3.75, 88],
    [3.50, 72],
    [3.92, 95],
    [3.67, 80],
    [3.80, 91]
])

# All rows, first column only — extract all CGPAs
all_cgpa = np_students[:, 0]
print(all_cgpa)
# Output: [3.75 3.5  3.92 3.67 3.8 ]
# : means "all rows", 0 means "column 0"

# All rows, second column only — extract all attendance
all_attendance = np_students[:, 1]
print(all_attendance)
# Output: [88. 72. 95. 80. 91.]

# First 3 rows, all columns — first 3 students
print(np_students[:3, :])
# Output:
# [[3.75 88. ]
#  [3.5  72. ]
#  [3.92 95. ]]

# All rows, both columns = full array (same as printing np_students)
print(np_students[:, :])

# Rows 1 to 3, only column 0 (cgpa of students 1,2,3)
print(np_students[1:4, 0])
# Output: [3.5  3.92 3.67]
```

> The comma is your GPS, then left of comma = which rows, right of comma = which columns. A `:` means give me everything in this direction.
> 

---

## 12. Element-wise Arithmetic on 2D Arrays

### The Concept

Just like 1D arrays, 2D arrays support element-wise arithmetic. You can add, subtract, multiply entire arrays — or combine an array with a single value, which applies to every element.

```python
import numpy as np

# Exam scores for 3 students across 3 subjects [Math, Physics, English]
scores = np.array([
    [75, 80, 65],
    [90, 55, 70],
    [60, 75, 85]
])

# Add 5 bonus marks to every score
print(scores + 5)
# Output:
# [[80 85 70]
#  [95 60 75]
#  [65 80 90]]

# Convert to percentage (out of 100, already is, just as example)
# Multiply by a conversion factor array — one value per column
conversion = np.array([1.0, 1.0, 1.0])  # each subject weight
print(scores * conversion)
# Output:
# [[75. 80. 65.]
#  [90. 55. 70.]
#  [60. 75. 85.]]

# Add two arrays element-wise — e.g., two exam sessions
session2 = np.array([
    [5, 10, 8],
    [3, 15, 5],
    [7, 5, 10]
])
total = scores + session2
print(total)
# Output:
# [[80 90 73]
#  [93 70 75]
#  [67 80 95]]
```

---

## 13. NumPy Basic Statistics

### The Concept

When you have a large dataset thousands of rows, you can't just look at it and understand it. You need **summary statistics**: numbers that describe the overall shape of the data.

NumPy has all of these built in. They all work on arrays, and for 2D arrays, you first extract the column you want, then run the function.

```python
import numpy as np

# 6 students: [cgpa, attendance, age]
np_data = np.array([
    [3.75, 88, 21],
    [3.50, 72, 20],
    [3.92, 95, 22],
    [3.67, 80, 21],
    [3.80, 91, 23],
    [3.20, 65, 20]
])

# Extract CGPA column (column 0)
cgpa = np_data[:, 0]
print(cgpa)
# Output: [3.75 3.5  3.92 3.67 3.8  3.2 ]

# Mean — average value
print(np.mean(cgpa))          # Output: 3.64

# Median — middle value when sorted
print(np.median(cgpa))        # Output: 3.71

# Standard deviation — how spread out the values are
print(np.std(cgpa))           # Output: ~0.245

# Min and Max
print(np.min(cgpa))           # Output: 3.2
print(np.max(cgpa))           # Output: 3.92

# Sum
print(np.sum(cgpa))           # Output: 21.84

# Correlation — do cgpa and attendance move together?
attendance = np_data[:, 1]
corr = np.corrcoef(cgpa, attendance)
print(corr)
# Output: 2x2 matrix. The value at [0,1] or [1,0] is the correlation.
# Close to 1 = strong positive. Close to 0 = no relationship. Close to -1 = inverse.

# If we want the correlation in just one number
corr_matrix = np.corrcoef(cgpa, attendance)
actual_corr = corr_matrix[0, 1] 
print("Correlation Value:",actual_corr)
# Output: Correlation Value: 0.9725036962810875

# The output is approximately 0.9721, which is extremely close to +1.0.
# This proves a "Strong Positive Correlation".
# Conclusion: Students with higher class attendance tend to secure higher CGPAs.
```

Correlation is a statistical measure that expresses the extent to which two variables are linearly related. In simple terms, it tells us: **"If variable A changes, how does variable B react?"**

We use `np.corrcoef(x, y)` in NumPy to calculate this. It returns a 2x2 matrix, where the value at `[0, 1]` or `[1, 0]` represents the correlation coefficient.

The correlation value always stays between **-1.0 and +1.0**:

1. **Positive Correlation (Close to +1.0):** Both variables move in the same direction. If one goes up, the other goes up.
    - *Example:* Higher Attendance leads to a Higher CGPA. (Our dataset shows a strong positive correlation of ~0.97!).
2. **No Correlation (Close to 0.0):** There is no relationship between the two variables. One changing does not affect the other.
    - *Example:* A student's shoe size vs. their CGPA.
3. **Negative Correlation (Close to -1.0):** The variables move in opposite directions. If one goes up, the other goes down.

---

## 14. Mean vs Median — When Each Matters

### The Concept

Mean and median both describe the "center" of your data. But they react very differently to extreme values called **outliers**.

> **Mean** = add all values, divide by count. Pulled strongly by outliers.
> 

> **Median** = the middle value when sorted. Barely affected by outliers.
> 

**Example:** Imagine 5 students' exam scores: `[72, 78, 80, 85, 350]`

The 350 is clearly a data entry error. Watch what happens:

```python
import numpy as np

scores = np.array([72, 78, 80, 85, 350])

print(np.mean(scores))     # Output: 133.0  ← pulled way up by 350
print(np.median(scores))   # Output: 80.0   ← not affected at all

# Mean says the average student scored 133 — that's misleading
# Median says the middle student scored 80 — that's the real story
```

```python
import numpy as np

# A more realistic example — monthly sales (in thousands)
sales = np.array([45, 52, 48, 50, 47, 200])
# 200 is a huge outlier (special event month)

print(np.mean(sales))      # Output: 73.67  ← distorted by 200
print(np.median(sales))    # Output: 49.0   ← true typical month

# If you report the mean, it looks like you usually sell 73k/month
# But the median shows the real typical performance: 49k/month
```

### Understanding Mean vs. Median (The Outlier Problem)

This code demonstrates a classic problem in data analytics: **when should we use the mean (average) and when should we use the median (middle value)?** The answer depends heavily on **outliers**.

1. **What is an outlier?**
    
    In our dataset, the sales for 5 months are very close to each other: `45, 52, 48, 50, 47` (all between 45k and 52k). However, in one specific month, sales suddenly jump to **200**. This could be due to a special event (festival, clearance sale, or a one-time bulk order). This unusually large (or small) value that deviates heavily from the rest of the data is called an **outlier**.
    
2. **Why the mean (average) misleads us here**
    
    The mean is calculated by adding all values and dividing by the total number of months:
    
    $$
    \text{Mean} = \frac{45 + 52 + 48 + 50 + 47 + 200}{6} = 73.67
    $$
    
    The problem: if a business owner looks at this mean (73.67k), they might assume, “Our shop usually generates around 73k every month.” But the shop performed below 73k in 5 out of the 6 months. The single outlier (`200`) pulls the mean upward and creates a distorted picture of typical performance.
    
3. **Why the median is the hero here**
    
    The median is calculated by sorting the numbers and picking the middle value:
    
    - Sorted data: `45, 47, 48, 50, 52, 200`
    - Since we have an even number of items (6 months), we take the average of the two middle numbers (48 and 50):
    
    $$
    \text{Median} = \frac{48 + 50}{2} = 49.0
    $$
    
    The median ignores the extreme value of `200` and focuses on the center of the distribution. It tells the business owner the truth: “On a typical month (without special events), the shop usually generates around 49k.”
    

**Real-world takeaway (when to use what?)**

- **Use mean** when your data is balanced and has **no extreme outliers**.
Example: average height/weight of students.
- **Use median** when your data contains **extreme outliers**.
Example: income distribution in a country (a few billionaires can distort the mean).

**Conclusion:** In this sales example, reporting the **median (49k)** is the smart choice to describe typical monthly performance, not the **mean (73.67k)**.

---

## 15. Practice Questions

### Easy

**Q1.** You have a list of 5 students' ages: `[19, 21, 20, 22, 18]`. Convert it to a NumPy array. Then:

- Print it
- Print its type
- Add 1 to every age in one line and print it (simulate next year)

Answer:

```python
import numpy as np

ages = np.array([19, 21, 20, 22, 18])
print(ages)                # [19 21 20 22 18]
print(type(ages))          # <class 'numpy.ndarray'>
print(ages + 1)            # [20 22 21 23 19]  — every age +1 at once
```

---

**Q2.** What will this print? Think first, then verify:

```python
import numpy as np
a = np.array([10, 20, 30])
b = [10, 20, 30]
print(a + a)
print(b + b)
```

Answer:

```
[20 40 60]      ← numpy: element-wise addition (10+10, 20+20, 30+30)
[10, 20, 30, 10, 20, 30]   ← list: concatenation (pasted together)
```

---

**Q3.** You have:

```python
import numpy as np
marks = np.array([55, 72, 88, 64, 91, 78, 45, 83])
```

Write code to print only the marks that are above 75.

Answer:

```python
import numpy as np
marks = np.array([55, 72, 88, 64, 91, 78, 45, 83])
mark=marks[marks>75]
print(mark)   # Output: [88 91 78 83]

### OR-

import numpy as np
marks = np.array([55, 72, 88, 64, 91, 78, 45, 83])
print(marks[marks > 75])   # Output: [88 91 78 83]
```

---

### Medium

**Q4.** You have data for 4 students: `[name_score, lab_score]`:

```python
import numpy as np
student_scores = np.array([
    [78, 85],
    [92, 88],
    [65, 70],
    [80, 95]
])
```

Write code to:

- Print the shape of this array
- Print the entire second row (student index 1)
- Print only the lab scores (second column) of all students
- Print the theory score of the third student (row 2, column 0)

Answer:

```python
import numpy as np
student_scores = np.array([[78, 85], [92, 88], [65, 70], [80, 95]])

print(student_scores.shape)         # Output: (4, 2)
print(student_scores[1])            # Output: [92 88]
print(student_scores[:, 1])         # Output: [85 88 70 95]  — all lab scores
print(student_scores[2, 0])         # Output: 65
```

---

**Q5.** Explain what happens when you run this and why:

```python
import numpy as np
mixed = np.array([100, 3.14, True, "pass"])
print(mixed)
print(mixed.dtype)
```

Answer:

```python
# Output: ['100' '3.14' 'True' 'pass']
# dtype: <U32

# Why: NumPy must pick ONE type for all elements.
# "pass" is a string, and strings are the most flexible — they can represent anything.
# So NumPy converts 100 → "100", 3.14 → "3.14", True → "True".
# No error, just silent conversion. This is why mixed-type arrays are dangerous.o
```

---

**Q6.** You have monthly sales data for two products across 6 months:

```python
import numpy as np
sales = np.array([
    [120, 95, 110, 88, 130, 105],   # Product A
    [ 80, 75,  90, 60,  95,  85]    # Product B
])

print(sales[0])
print 
```

Write code to:

- Print Product A's sales only (row 0)
- Print Product B's sales only (row 1)
- Print sales for both products in months 2, 3, 4 (columns 2 to 4)
- Calculate and print the mean monthly sales for Product A

Answer:

```python
import numpy as np
sales = np.array([[120, 95, 110, 88, 130, 105],
                  [ 80, 75,  90, 60,  95,  85]])

print(sales[0])           # [120  95 110  88 130 105]
print(sales[1])           # [80 75 90 60 95 85]
print(sales[:, 2:5])      # columns 2,3,4 for both rows
# Output: [[110  88 130]
#          [ 90  60  95]]
print(np.mean(sales[0]))  # Output: 108.0
```

---

### Hard / Think Deeper

**Q7.** You have CGPA data for 100 students. You notice the mean is 3.95 but the median is 3.42. What does this tell you about the data? Which statistic should you report as the "typical" CGPA? Why?

Answer:

When the mean (3.95) is much higher than the median (3.42), it means there are a few students with very high CGPAs (outliers near 4.0) pulling the mean up. The majority of students are clustered around 3.42. You should report the **median** as the "typical" CGPA, because it represents the actual middle of the distribution and is not distorted by the high-achieving outliers.

---

**Q8.** Predict the output of this code step by step, and explain the logic behind each line:

```python
import numpy as np
scores = np.array([55, 72, 88, 64, 91, 78, 45, 83])

mask = scores >= 70
print(mask)
print(scores[mask])
print(len(scores[mask]))
print(np.mean(scores[scores >= 70]))
```

Answer:

```python
# mask = scores >= 70
# [False  True  True False  True  True False  True]
#   55    72    88    64    91    78    45    83

# scores[mask] — only elements where mask is True
# Output: [72 88 91 78 83]

# len(scores[mask])
# Output: 5  — 5 values passed the filter

# np.mean(scores[scores >= 70])
# mean of [72 88 91 78 83] = (72+88+91+78+83)/5 = 412/5 = 82.4
# Output: 82.4
```

---

**Q9.** You have exam data for 5 students across 3 subjects:

```python
import numpy as np
exams = np.array([
    [75, 82, 68],
    [90, 88, 92],
    [60, 55, 70],
    [85, 79, 81],
    [72, 66, 74]
])
```

Write code to:

- Find the mean score for each subject (column-wise mean using `np.mean(arr, axis=0)`)
- Find the total score for each student (row-wise sum using `np.sum(arr, axis=1)`)
- Find the highest-scoring student (row with max total)
- Find all students whose average across subjects is above 75

Answer:

```python
import numpy as np
exams = np.array([[75, 82, 68], [90, 88, 92], [60, 55, 70],
                  [85, 79, 81], [72, 66, 74]])

# Mean per subject (column-wise)
print(np.mean(exams, axis=0))   # [76.4 74.  77. ]

# Total per student (row-wise)
totals = np.sum(exams, axis=1)
print(totals)                   # [225 270 185 245 212]

# Highest scoring student
# np.argmax() finds the highest value and returns its index position
print(np.argmax(totals))        # 1  (student at index 1 has max total: 270)

# Students with average above 75
student_avgs = np.mean(exams, axis=1)
print(student_avgs[student_avgs > 75])   # [80. 90. 81.67]
# Students 0 (80), 1 (90), 3 (81.67) qualify
```

### Understanding `axis` in NumPy (2D Arrays)

In NumPy, a 2D array (matrix) is a grid made of **Rows** and **Columns**. When you want to perform operations like `np.mean()`, `np.sum()`, `np.min()`, or `np.max()`, NumPy needs to know the **direction** in which it should perform the calculation. This direction is defined using the `axis` parameter.

### 1. `axis=0` (Column-Wise Operation)

- **Direction:** Vertical
- **How it works:** NumPy collapses the rows and calculates the result for **each column individually**.
- **Real-World Analogy:** If your rows represent *Students* and columns represent *Subjects*, using `axis=0` will give you the statistics for **each subject across all students**.

Python

```
# Example: Finding the average score for each subject
subject_means = np.mean(exams, axis=0)
# Result: [Mean_of_Sub1, Mean_of_Sub2, Mean_of_Sub3]
```

### 2. `axis=1` (Row-Wise Operation)

- **Direction:** Horizontal
- **How it works:** NumPy collapses the columns and calculates the result for **each row individually**.
- **Real-World Analogy:** If your rows represent *Students* and columns represent *Subjects*, using `axis=1` will give you the statistics for **each individual student across all their subjects**.

Python

```
# Example: Finding the total score achieved by each student
student_totals = np.sum(exams, axis=1)
# Result: [Total_Student0, Total_Student1, Total_Student2, ...]
```

### Why do we use `axis` instead of manual Slicing (`:`)?

While you can use slicing (`exams[:, 0]`) to manually extract and calculate data for small datasets, it becomes impossible when dealing with real-world Big Data (e.g., a matrix with 500,000 rows and 1,000 columns).

Passing the `axis` parameter allows NumPy to utilize highly optimized C-language loops under the hood, processing millions of rows instantly with just **one single line of code**.

---

## 16. Chapter Summary Table

| Concept | Syntax | Example | Notes |
| --- | --- | --- | --- |
| Import NumPy | `import numpy as np` | — | Always alias as `np` |
| Create 1D array | `np.array(list)` | `np.array([1,2,3])` | Pass a list in |
| Create 2D array | `np.array(list_of_lists)` | `np.array([[1,2],[3,4]])` | Each sublist = one row |
| Check type | `type(arr)` | → `numpy.ndarray` | ndarray = n-dimensional |
| Check shape | `arr.shape` | → `(5, 2)` | Attribute, no brackets! |
| Element-wise op | `arr * 2` | each element × 2 | Works with +, -, *, /,* * |
| Between two arrays | `arr1 + arr2` | element by element | Must be same shape |
| Single element 1D | `arr[i]` | `arr[0]` | Same as list indexing |
| Slice 1D | `arr[start:end]` | `arr[2:5]` | End not included |
| Single element 2D | `arr[row, col]` | `arr[1, 0]` | Comma syntax preferred |
| Entire row | `arr[i, :]` | `arr[2, :]` | `:` = all columns |
| Entire column | `arr[:, j]` | `arr[:, 1]` | `:` = all rows |
| Slice rows+cols | `arr[r1:r2, c1:c2]` | `arr[0:2, 1:3]` | Rectangle selection |
| Boolean filter | `arr[arr > value]` | `arr[arr > 80]` | Filters in one step |
| Boolean mask | `arr > value` | → `[True, False, ...]` | Step 1 of boolean subset |
| Mean | `np.mean(arr)` | → average | Affected by outliers |
| Median | `np.median(arr)` | → middle value | Robust against outliers |
| Std deviation | `np.std(arr)` | → spread | How far values deviate |
| Min / Max | `np.min(arr)` / `np.max(arr)` |  | Smallest / largest |
| Sum | `np.sum(arr)` |  | Total of all elements |
| Correlation | `np.corrcoef(a, b)` | → 2x2 matrix | [0,1] is the key value |
| Row-wise op | `np.sum(arr, axis=1)` | sum each row | axis=1 = across columns |
| Column-wise op | `np.mean(arr, axis=0)` | mean each column | axis=0 = across rows |
| Single type rule | — | `np.array([1,"x",True])` → all strings | Silently converts types |
|   • on list | `list + list` | concatenation | Pasted together |
|   • on array | `array + array` | element-wise add | Completely different! |

---

## Mental Model — The Full Picture

```
NumPy exists because Python lists cannot do math.
A NumPy array looks like a list but behaves like a math object.

1D ARRAY — a single row of numbers:
    np.array([72, 85, 91, 60, 78])
    Indexed the same as a list: arr[0], arr[-1], arr[2:5]
    But you can do math on the whole thing: arr * 2, arr + 5

2D ARRAY — a table (rows × columns):
    np.array([[r0c0, r0c1],
              [r1c0, r1c1],
              [r2c0, r2c1]])

    Navigate with comma: arr[row, column]
    Use : for "all":    arr[:, 0]   → entire first column
                        arr[1, :]   → entire second row
                        arr[0:3, 1] → rows 0,1,2 of column 1

BOOLEAN SUBSETTING — filter without a loop:
    mask = arr > 80           → [False True True False True]
    arr[mask]                 → only the True values
    One-liner: arr[arr > 80]  → same result

TYPE RULE — NumPy picks ONE type for the whole array:
    [1, 2.5, True]    → all float64     (most flexible number)
    [1, "x", True]    → all string      (most flexible overall)
    No error, just silent conversion. Always check dtype.

OPERATOR RULE — same symbol, different meaning:
    list + list    → paste (concatenation)
    array + array  → math (element-wise addition)

STATISTICS:
    np.mean()     → average (sensitive to outliers)
    np.median()   → middle value (safe from outliers)
    np.std()      → spread of the data
    np.corrcoef() → how two variables move together
    axis=0 → operate down each column (collapse rows)
    axis=1 → operate across each row  (collapse columns)
```