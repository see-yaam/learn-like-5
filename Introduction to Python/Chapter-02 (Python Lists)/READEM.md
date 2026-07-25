---

# **Chapter-02 (Python Lists)**

## Table of Contents

1. [Why Lists Exist](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#1-why-lists-exist)
2. [Creating a List](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#2-creating-a-list)
3. [Lists with Mixed Types](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#3-lists-with-mixed-types)
4. [List of Lists (Nested Lists)](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#4-list-of-lists-nested-lists)
5. [Subsetting — Accessing Elements by Index](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#5-subsetting--accessing-elements-by-index)
6. [Negative Indexing](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#6-negative-indexing)
7. [Slicing — Selecting Multiple Elements](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#7-slicing--selecting-multiple-elements)
8. [Subsetting a List of Lists](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#8-subsetting-a-list-of-lists)
9. [Changing List Elements](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#9-changing-list-elements)
10. [Adding Elements to a List](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#10-adding-elements-to-a-list)
11. [Removing Elements from a List](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#11-removing-elements-from-a-list)
12. [The Reference Trap — Copying Lists Correctly](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#12-the-reference-trap--copying-lists-correctly)
13. [Practice Questions](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#13-practice-questions)
14. [Chapter Summary Table](https://github.com/see-yaam/learn-like-5/blob/main/Introduction%20to%20Python/Chapter-02%20(Python%20Lists)/READEM.md#14-chapter-summary-table)

---

## 1. Why Lists Exist

### The Problem

You already know that variables store one value at a time.

```python
player1_run = 45
player2_run = 78
player3_run = 12
player4_run = 91
```

This works for 4 players. What about a full squad of 15? Or tracking 365 days of temperature data? You'd need 365 variables.

### The Solution

A **list** lets you store many values under one single name.

```python
runs = [45, 78, 12, 91, 33]
```

One name. Five values. That's a list.

> A list is a container that holds multiple values in a specific order.
> 

---

## 2. Creating a List

### Syntax

```python
list_name = [value1, value2, value3]
```

Square brackets `[]` — that's how Python knows it's a list.

### Code

```python
# A cricket team's run scores in one innings
player1_run = 45
player2_run = 78
player3_run = 12
player4_run = 91
player5_run = 33

# Store all scores in one list
runs = [player1_run, player2_run, player3_run, player4_run, player5_run]

print(runs)
# Output: [45, 78, 12, 91, 33]

# Check the type
print(type(runs))
# Output: <class 'list'>
```

---

## 3. Lists with Mixed Types

### The Concept

A list can hold any combination of data types — int, float, str, bool, even other lists. No restrictions.

```python
# Player name paired with their run score
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]
```

Now each name is paired with its score, in order. This is way more readable than just numbers.

### Code

```python
# List with mixed types — string + int pairs
player_info = [
    "Shakib",  45,
    "Tamim",   78,
    "Mushfiq", 12,
    "Liton",   91,
    "Mehidy",  33
]

print(player_info)
# Output: ['Shakib', 45, 'Tamim', 78, 'Mushfiq', 12, 'Liton', 91, 'Mehidy', 33]
```

---

## 4. List of Lists (Nested Lists)

### The Concept

Instead of mixing names and scores in one flat list, you can group each pair into its own sublist. Then store all those sublists in one outer list.

This is called a **nested list** — a list inside a list.

```
Flat list:   ["Shakib", 45, "Tamim", 78]
Nested list: [["Shakib", 45], ["Tamim", 78]]
```

Nested lists are better when each group of data belongs together logically.

### Code

```python
# List of lists — each sublist is [player_name, runs_scored]
squad = [
    ["Shakib",  45],
    ["Tamim",   78],
    ["Mushfiq", 12],
    ["Liton",   91],
    ["Mehidy",  33]
]

print(squad)
# Output: [['Shakib', 45], ['Tamim', 78], ['Mushfiq', 12], ['Liton', 91], ['Mehidy', 33]]

print(type(squad))
# Output: <class 'list'>

print(type(squad[0]))
# Output: <class 'list'>  — the first element is itself a list
```

---

## 5. Subsetting — Accessing Elements by Index

### The Concept

Every element in a list has an **index** — its position number. Python starts counting from **0**, not 1.

```
List:    ["Shakib", 45, "Tamim", 78, "Mushfiq", 12]
Index:       0       1     2      3      4        5
```

To grab one element, write the list name followed by the index inside square brackets.

```python
player_info[0]   # "Shakib"
player_info[1]   # 45
player_info[4]   # "Mushfiq"
```

> The first element is always at index 0. This trips up almost every beginner once.
> 

### Code

```python
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]

# First player's name (index 0)
print(player_info[0])    # Output: Shakib

# Tamim's run score (index 3)
print(player_info[3])    # Output: 78

# Liton's name (index 6)
print(player_info[6])    # Output: Liton
```

---

## 6. Negative Indexing

### The Concept

Python also lets you count from the **end** of the list using negative numbers.

```
List:    ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]
Neg idx:    -10     -9    -8     -7     -6       -5    -4     -3    -2      -1
```

- `-1` is always the last element. `-2` is second to last. And so on.

This is useful when you want the last few items without counting the total length.

```python
player_info[-1]   # 33  — last element (Mehidy's score)
player_info[-2]   # "Mehidy"  — second to last
```

### Code

```python
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]

# Last element using negative index
print(player_info[-1])    # Output: 33

# Second to last
print(player_info[-2])    # Output: Mehidy

# These two lines give the same result:
print(player_info[9])     # Output: 33
print(player_info[-1])    # Output: 33  — same thing, easier to write
```

---

## 7. Slicing — Selecting Multiple Elements

### The Concept

Instead of grabbing one element, slicing lets you grab a **range** of elements at once. The result is a new list.

```python
list_name[start:end]
```

**Critical rule:** `start` index is **included**, `end` index is **excluded**.

```
player_info[2:6]  →  elements at index 2, 3, 4, 5  (NOT 6)
```

You can also leave out the start or end:

```python
player_info[:4]   # from beginning up to (not including) index 4
player_info[6:]   # from index 6 to the very end
player_info[:]    # entire list (used for copying)
```

### Code

```python
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]

# First 4 elements — first two players (name + score)
top_two = player_info[:4]
print(top_two)
# Output: ['Shakib', 45, 'Tamim', 78]

# Last 4 elements — last two players
last_two = player_info[-4:]
print(last_two)
# Output: ['Liton', 91, 'Mehidy', 33]

# Middle slice — Tamim and Mushfiq
middle = player_info[2:6]
print(middle)
# Output: ['Tamim', 78, 'Mushfiq', 12]
```

---

## 8. Subsetting a List of Lists

### The Concept

When your list contains other lists, you need **two** sets of square brackets to reach inside.

```python
squad[outer_index][inner_index]
```

First bracket picks the sublist. Second bracket picks the element inside that sublist.

```
squad[3]      →  ["Liton", 91]      (the whole sublist)
squad[3][1]   →  91                 (the int inside that sublist)
```

### Code

```python
squad = [
    ["Shakib",  45],   # index 0
    ["Tamim",   78],   # index 1
    ["Mushfiq", 12],   # index 2
    ["Liton",   91],   # index 3
    ["Mehidy",  33]    # index 4
]

# Get Liton's full sublist
print(squad[3])        # Output: ['Liton', 91]

# Get just Liton's run score
print(squad[3][1])     # Output: 91

# Get Tamim's name
print(squad[1][0])     # Output: Tamim

# Get Mushfiq's run score
print(squad[2][1])     # Output: 12
```

---

## 9. Changing List Elements

### The Concept

Lists are **mutable,** meaning you can change their contents after creation. Variables are not mutable in the same way, reassigning a variable just points it to a new value. But with lists, you can go inside and swap specific elements.

```python
list_name[index] = new_value
```

You can also update a whole slice at once:

```python
list_name[start:end] = [new_value1, new_value2]
```

### Code

```python
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]

# Mushfiq scored more — update his score (index 5)
player_info[5] = 55
print(player_info[5])   # Output: 55

# Tamim's name was misspelled — fix it (index 2)
player_info[2] = "Tamim Al Bahar"
print(player_info[2])   # Output: Tamim Al Bahar

# Update a whole slice — replace first two elements (Shakib's name + score)
player_info[0:2] = ["Shakib Al Hasan", 67]
print(player_info[:2])  # Output: ['Shakib Al Hasan', 67]
```

---

## 10. Adding Elements to a List

### The Concept

You cannot insert elements directly into a list using `+` on its own — `+` creates a **new** list by joining two lists together.

```python
new_list = existing_list + [new_item1, new_item2]
```

The original list is not changed. The result is stored in a new variable (or the same one if you reassign).

### Code

```python
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12, "Liton", 91, "Mehidy", 33]

# A new player joined the squad — create an extended list
squad_v2 = player_info + ["Taskin", 8]
print(squad_v2[-2:])    # Output: ['Taskin', 8]

# Add one more player on top
squad_v3 = squad_v2 + ["Shoriful", 14]
print(squad_v3[-2:])    # Output: ['Shoriful', 14]

# Original list is unchanged
print(player_info[-1])  # Output: 33  — still Mehidy's score
```

---

## 11. Removing Elements from a List

### The Concept

Use the `del` keyword to remove an element by its index.

```python
del list_name[index]
```

**Important:** After deletion, all elements after the removed one **shift left** by one index. So if you delete index 2, what was index 3 becomes the new index 2.

This means if you want to delete two consecutive elements (like a name and its score), you delete the first one then delete the same index again (because the second element has now moved up).

### Code

```python
player_info = ["Shakib", 45, "Tamim", 78, "Mushfiq", 12,
               "Liton", 91, "Mehidy", 33, "Taskin", 8]

# Remove Taskin from the squad (index 10 = name, index 11 = score)
del player_info[10]   # removes "Taskin"
del player_info[10]   # removes 8 (which shifted to index 10)

print(player_info)
# Output: ['Shakib', 45, 'Tamim', 78, 'Mushfiq', 12, 'Liton', 91, 'Mehidy', 33]
```

---

## 12. The Reference Trap — Copying Lists Correctly

### The Concept (This is the Most Important Part of This Chapter)

When you create a list in Python, the variable doesn't hold the list directly. It holds a **reference** — basically, the memory address of where the list lives.

Think of it like this: the list is a house. The variable is not the house — it's just the **address** of the house written on a sticky note.

When you do `y = x`, you're copying the address — **not the house**. Both `x` and `y` now point to the same house. If you change something in the house using `y`, it also changes when you look through `x`. They are the same house.

```python
x = ["a", "b", "c"]
y = x            # y gets the same address as x

y[1] = "z"       # you go into the house and change "b" to "z"

print(x)         # ['a', 'z', 'c']  — x sees the change too!
print(y)         # ['a', 'z', 'c']
```

### How to Actually Copy a List

To make a real independent copy a new house with the same contents. Use one of these two methods:

```python
y = list(x)   # method 1: using the list() function
y = x[:]      # method 2: slicing the whole list
```

Now `x` and `y` point to different houses. Changing one does not affect the other.

### Code

```python
original_scores = [45, 78, 12, 91, 33]

# WRONG way — both variables point to the same list
backup = original_scores
backup[0] = 0
print(original_scores[0])   # Output: 0 — original got changed too!

# RIGHT way — create a new independent copy
original_scores = [45, 78, 12, 91, 33]   # reset

safe_backup = list(original_scores)    # method 1
# OR
safe_backup = original_scores[:]       # method 2 — both work the same

safe_backup[0] = 0
print(original_scores[0])   # Output: 45 — original is safe
print(safe_backup[0])        # Output: 0  — only the copy changed
```

---

## 13. Practice Questions

> Original questions based on Chapter 2 concepts.
> 

### Easy

**Q1.** Create a list called `cgpa` with the values 3.85, 3.50, 3.92, 3.67, 3.78. Print the third value.

Answer: 

```python
cgpa = [3.85, 3.50, 3.92, 3.67, 3.78]
print(cgpa[2])   # Output: 3.92  (index 2 is the third item)
```

---

**Q2.** What is the index of the last element in a list of 7 items? What is its negative index?

Answer:  A list of 7 items has indices 0 through 6. The last element is at index `6`. Its negative index is `-1`.

---

**Q3.** Given `subjects = ["Math", "Physics", "CSE", "English"]`, what does `subjects[1:3]` return?

Answer: 

```python
subjects = ["Math", "Physics", "CSE", "English"]
print(subjects[1:3])
# Output: ['Physics', 'CSE']
# index 1 included, index 3 excluded
```

---

### Medium

**Q4.** You have this list:

```python
leaderboard = ["Arif", 320, "Sadia", 415, "Tanvir", 289]
```

Write code to:

- Print the name at index 2
- Print the score of the last person using a negative index
- Slice out only the names (every other element starting from 0)

Answer: 

```python
leaderboard = ["Arif", 320, "Sadia", 415, "Tanvir", 289]

print(leaderboard[2])    # Output: Sadia
print(leaderboard[-1])   # Output: 289

# Slice only names — index 0, 2, 4
# (slicing every other element uses step syntax: [start:end:step])
print(leaderboard[0::2])   # Output: ['Arif', 'Sadia', 'Tanvir']
```

---

**Q5.** You have a nested list:

```python
semester = [["CSE 1111", 3.0], ["MAT 1151", 3.0], ["PHY 1151", 3.0]]
```

Write code to:

- Print the full sublist for MAT 1151
- Print only the credit hours of PHY 1151

Answer: 

```python
semester = [["CSE 1111", 3.0], ["MAT 1151", 3.0], ["PHY 1151", 3.0]]

print(semester[1])       # Output: ['MAT 1151', 3.0]
print(semester[2][1])    # Output: 3.0
```

**Q6.** You have:

```python
temps = [36.5, 37.1, 38.4, 36.8, 39.0]
```

- Change the last temperature to 37.5
- Add two new readings `[36.9, 37.2]` at the end
- Delete the third element (38.4)
- Print the final list

Answer: 

```python
temps = [36.5, 37.1, 38.4, 36.8, 39.0]

temps[-1] = 37.5                  # change last reading
temps = temps + [36.9, 37.2]      # add two new readings
del temps[2]                      # delete 38.4 (was at index 2)

print(temps)
# Output: [36.5, 37.1, 36.8, 37.5, 36.9, 37.2]
```

---

### Hard / Think Deeper

**Q7.** What will the output be? Explain why:

```python
a = [1, 2, 3]
b = a
b.append(4)      # .append() adds to the end
print(a)
```

Answer:

```python
# Output: [1, 2, 3, 4]
# Because b = a copies the reference, not the list.
# Both a and b point to the same list in memory.
# When b.append(4) runs, it modifies the shared list.
# So a sees the change too.
```

---

**Q8.** Fix this code so that changing `backup` does not affect `data`:

```python
data = [10, 20, 30, 40]
backup = data
backup[0] = 999
print(data)   # should still print [10, 20, 30, 40]
```

Answer:

```python
data = [10, 20, 30, 40]
backup = data[:]    # or: backup = list(data)
backup[0] = 999
print(data)   # Output: [10, 20, 30, 40]  — safe now
```

---

**Q9.** You have a list of UIU courses with credit hours:

```python
courses = [
    ["CSE 1111", 3.0],
    ["CSE 1112", 1.5],
    ["MAT 1151", 3.0],
    ["PHY 1151", 3.0],
    ["PHY 1152", 1.5]
]
```

Write code to:

- Print the name of the 3rd course
- Print the credit hour of the last course using negative indexing
- Change the credit hour of "CSE 1112" to 2.0
- Add a new course `["ENG 1011", 3.0]` at the end
- Print the total number of items in the outer list (use `len()`)

Answer:

```python
courses = [
    ["CSE 1111", 3.0],
    ["CSE 1112", 1.5],
    ["MAT 1151", 3.0],
    ["PHY 1151", 3.0],
    ["PHY 1152", 1.5]
]

print(courses[2][0])      # Output: MAT 1151
print(courses[-1][1])     # Output: 1.5
courses[1][1] = 2.0       # change CSE 1112 credit hour
courses = courses + [["ENG 1011", 3.0]]   # add new course
print(len(courses))       # Output: 6
```

---

## 14. Chapter Summary Table

| Concept | Syntax | Example | Output |
| --- | --- | --- | --- |
| Create list | `[a, b, c]` | `x = [1, 2, 3]` | `[1, 2, 3]` |
| Mixed types | any combo | `["Shakib", 45, True]` | works fine |
| Nested list | `[[a,b],[c,d]]` | `[["Arif", 3.8], ["Sadia", 3.9]]` | list of lists |
| Index access | `list[i]` | `x[0]` | first element |
| Negative index | `list[-i]` | `x[-1]` | last element |
| Slice | `list[s:e]` | `x[1:3]` | index 1, 2 (not 3) |
| Slice from start | `list[:e]` | `x[:3]` | index 0, 1, 2 |
| Slice to end | `list[s:]` | `x[2:]` | index 2 onwards |
| Nested access | `list[i][j]` | `squad[2][1]` | inner element |
| Change element | `list[i] = val` | `x[0] = 9` | updates in place |
| Add elements | `list + [new]` | `x + [4, 5]` | new combined list |
| Delete element | `del list[i]` | `del x[1]` | removes element |
| Copy (wrong) | `y = x` | — | both point to same list |
| Copy (correct) | `y = x[:]` or `list(x)` | — | independent copy |

---

---

```
A list is a train.
Each carriage holds one value.
The whole train has one name.
You can board any carriage, swap its contents, add new ones, or unhook them.

INDEXING — every carriage has a number:

    train  =  [ "Shakib",   45,   "Tamim",   78,   "Liton",   91  ]
    forward:      0          1       2          3      4          5
    backward:    -6         -5      -4         -3     -2         -1

    train[0]    →  "Shakib"    (first carriage, from the front)
    train[-1]   →  91          (last carriage, from the back)
    train[2]    →  "Tamim"     (third carriage — remember, count from 0)

SLICING — grab a section of the train:

    train[start : end]    →  start is included, end is NOT

    train[0:4]   →  ["Shakib", 45, "Tamim", 78]   (carriages 0,1,2,3)
    train[:4]    →  same as above (omit start = begin from 0)
    train[4:]    →  ["Liton", 91]                  (from 4 to last)
    train[-2:]   →  ["Liton", 91]                  (last 2 carriages)

NESTED LISTS — a carriage holding a smaller train:

    squad = [["Shakib", 45], ["Tamim", 78], ["Liton", 91]]

    squad[1]       →  ["Tamim", 78]   (second inner train)
    squad[1][0]    →  "Tamim"         (first item of second inner train)
    squad[1][1]    →  78              (second item of second inner train)

    Two keys: first opens the outer, second opens the inner.

MANIPULATION — three operations:

    Change  →  train[i] = new_value        (swap one carriage's content)
    Add     →  train + [new, items]        (returns a NEW longer train)
    Delete  →  del train[i]                (unhook a carriage — rest shift forward!)

    After del, every carriage after the removed one
    gets a new number. Index 3 becomes index 2. Watch out.

COPYING — the most dangerous part:

    ┌──────────────────────────────────────────────────────┐
    │  y = x           WRONG — two names, one train        │
    │                  change y → x changes too            │
    │                                                      │
    │  y = x[:]        RIGHT — a brand new train           │
    │  y = list(x)     RIGHT — same result, different way  │
    │                  change y → x stays safe             │
    └──────────────────────────────────────────────────────┘

    Python variables store addresses, not values.
    y = x copies the address.
    y = x[:] builds a new train at a new address.
```

---
