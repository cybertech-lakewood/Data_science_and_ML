#  Week 5 – Day 1: Pandas DataFrame Operations & NumPy Introduction

> **Learning Journey** | Python for Data Science | cybertech-lakewood

---

## 📋 Table of Contents

1. [DataFrame Merging Techniques](#1-dataframe-merging-techniques)
2. [Filtering Data Based on Conditions](#2-filtering-data-based-on-conditions)
3. [Managing DataFrame Columns](#3-managing-dataframe-columns)
4. [Grouping and Aggregation](#4-grouping-and-aggregation)
5. [File Path Management & Reading Excel Files](#5-file-path-management--reading-excel-files)
6. [Introduction to NumPy](#6-introduction-to-numpy)
7. [Array Attributes](#7-array-attributes)
8. [Array Operations](#8-array-operations)
9. [Aggregation Functions](#9-aggregation-functions)
10. [Indexing](#10-indexing)
11. [Array Manipulation – Reshape](#11-array-manipulation--reshape)
12. [Concatenation in NumPy](#12-concatenation-in-numpy)
13. [Broadcasting in NumPy](#13-broadcasting-in-numpy)

---

## 1. DataFrame Merging Techniques

Merging combines two DataFrames based on a shared column — similar to SQL JOINs. The `how` parameter controls which rows are kept.

```python
import pandas as pd

df1 = pd.DataFrame({
    'employee_id': [1, 2, 3],
    'name': ['Alice', 'Bob', 'Carol']
})

df2 = pd.DataFrame({
    'employee_id': [1, 2, 4],
    'department': ['HR', 'IT', 'Finance']
})

# Inner join — keeps only matching rows in both DataFrames
inner = pd.merge(df1, df2, on='employee_id', how='inner')

# Left join — keeps all rows from df1, NaN where df2 has no match
left = pd.merge(df1, df2, on='employee_id', how='left')

# Outer join — keeps all rows from both DataFrames
outer = pd.merge(df1, df2, on='employee_id', how='outer')

print("Inner Join:\n", inner)
print("\nLeft Join:\n", left)
print("\nOuter Join:\n", outer)
```

**Output (Inner Join):**
```
   employee_id   name department
0            1  Alice         HR
1            2    Bob         IT
```

> 💡 Use `inner` when you only want records that exist in both tables. Use `left` to keep all records from your primary DataFrame even if the secondary one has no match.

---

### Joining DataFrames by Index

When your key is the DataFrame index rather than a column, use `.join()` or merge on the index directly.

```python
df_a = pd.DataFrame(
    {'salary': [50000, 60000, 70000]},
    index=[1, 2, 3]
)

df_b = pd.DataFrame(
    {'department': ['HR', 'IT', 'Finance']},
    index=[1, 2, 3]
)

# Join on index (default is left join)
result = df_a.join(df_b)
print(result)
```

**Output:**
```
   salary department
1   50000         HR
2   60000         IT
3   70000    Finance
```

---

### DataFrame `.join()` Explained

`.join()` is a shortcut for merging on the index. It is cleaner when both DataFrames share the same index.

| Method | Key Type | Best For |
|--------|----------|----------|
| `pd.merge()` | Column or Index | Flexible joins on any column |
| `df.join()` | Index only | Quick index-based joins |

---

## 2. Filtering Data Based on Conditions

Filtering lets you select rows that meet a specific condition using boolean expressions.

```python
import pandas as pd

df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Carol', 'David'],
    'age': [25, 30, 22, 35],
    'score': [88, 72, 95, 60]
})

# Single condition — age greater than 25
above_25 = df[df['age'] > 25]

# Multiple conditions — age > 25 AND score > 70
filtered = df[(df['age'] > 25) & (df['score'] > 70)]

# OR condition — age < 25 OR score > 90
either = df[(df['age'] < 25) | (df['score'] > 90)]

print("Above 25:\n", above_25)
print("\nAge > 25 AND Score > 70:\n", filtered)
```

> 💡 Always wrap each condition in parentheses `()` when combining with `&` (AND) or `|` (OR).

---

## 3. Managing DataFrame Columns

You can add, rename, reorder, and drop columns to shape your DataFrame.

```python
import pandas as pd

df = pd.DataFrame({
    'name': ['Alice', 'Bob'],
    'score': [88, 72]
})

# Add a new column
df['grade'] = ['A', 'B']

# Rename a column
df.rename(columns={'score': 'exam_score'}, inplace=True)

# Drop a column
df.drop(columns=['grade'], inplace=True)

# Reorder columns
df = df[['name', 'exam_score']]

print(df)
```

> 💡 `inplace=True` modifies the DataFrame directly without needing to reassign it.

---

## 4. Grouping and Aggregation

`groupby()` splits the DataFrame into groups and applies an aggregation function to each group — great for summary statistics.

```python
import pandas as pd

df = pd.DataFrame({
    'department': ['HR', 'IT', 'HR', 'IT', 'Finance'],
    'employee': ['Alice', 'Bob', 'Carol', 'David', 'Eve'],
    'salary': [50000, 70000, 55000, 80000, 65000]
})

# Group by department and calculate mean salary
mean_salary = df.groupby('department')['salary'].mean()

# Multiple aggregations at once
summary = df.groupby('department')['salary'].agg(['mean', 'sum', 'count'])

print("Mean Salary by Department:\n", mean_salary)
print("\nSummary:\n", summary)
```

**Output:**
```
department
Finance    65000.0
HR         52500.0
IT         75000.0
Name: salary, dtype: float64
```

> 💡 `.agg()` lets you apply multiple aggregation functions in one step, returning a cleaner summary table.

---

## 5. File Path Management & Reading Excel Files

Managing file paths properly ensures your scripts work across different operating systems and environments.

```python
import pandas as pd
import os

# Build a file path safely using os.path.join (works on Windows & Linux/Mac)
folder = 'data'
filename = 'employees.xlsx'
file_path = os.path.join(folder, filename)

print("File path:", file_path)  # data/employees.xlsx (Linux/Mac) or data\employees.xlsx (Windows)

# Read an Excel file
df = pd.read_excel(file_path)

# Read a specific sheet by name
df_sheet = pd.read_excel(file_path, sheet_name='Sheet1')

# Read with specific columns only
df_cols = pd.read_excel(file_path, usecols=['name', 'salary'])

print(df.head())
```

> 💡 Always use `os.path.join()` instead of manually typing `/` or `\` in paths — it makes your code portable across operating systems.

---

## 6. Introduction to NumPy

NumPy (Numerical Python) provides fast, efficient arrays for numerical computation. It is the backbone of data science in Python.

### 1D Array from a Python List

```python
import numpy as np

python_list = [10, 20, 30, 40, 50]
arr_1d = np.array(python_list)

print(arr_1d)        # [10 20 30 40 50]
print(type(arr_1d))  # <class 'numpy.ndarray'>
```

> 💡 A 1D array is like a single row of values — similar to a Python list, but much faster for math operations.

---

### 2D Array from a Nested Python List

```python
import numpy as np

nested_list = [[1, 2, 3],
               [4, 5, 6]]

arr_2d = np.array(nested_list)
print(arr_2d)
```

**Output:**
```
[[1 2 3]
 [4 5 6]]
```

> 💡 A 2D array is like a table with rows and columns. The outer list holds rows and each inner list is a row.

---

## 7. Array Attributes

Every NumPy array has built-in attributes that describe its structure.

```python
import numpy as np

arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print("Shape:", arr.shape)      # (2, 3) → 2 rows, 3 columns
print("Size:", arr.size)        # 6 → total number of elements
print("Data type:", arr.dtype)  # int64 → integer values
```

| Attribute | Returns | Meaning |
|-----------|---------|---------|
| `.shape` | `(rows, cols)` | Dimensions of the array |
| `.size` | integer | Total number of elements |
| `.dtype` | data type | Type of values stored (int, float, etc.) |

---

## 8. Array Operations

NumPy performs element-wise arithmetic — operations apply to every element automatically without needing a loop.

```python
import numpy as np

a = np.array([10, 20, 30])
b = np.array([1, 2, 3])

# Addition
print("Addition:", a + b)        # [11 22 33]

# Subtraction
print("Subtraction:", a - b)     # [ 9 18 27]

# Multiplication
print("Multiplication:", a * b)  # [10 40 90]
```

> 💡 This is called **vectorization** — NumPy applies the operation to all elements at once, which is much faster than a Python `for` loop.

---

## 9. Aggregation Functions

Aggregation functions reduce an array to a single summary value.

```python
import numpy as np

arr = np.array([5, 10, 15, 20, 25])

print("Sum:", np.sum(arr))   # 75
print("Max:", np.max(arr))   # 25
print("Min:", np.min(arr))   # 5
```

> 💡 These are useful for quickly summarizing datasets — total sales, highest score, lowest temperature, etc.

---

## 10. Indexing

NumPy uses zero-based indexing. For 2D arrays, use `[row, column]` notation.

```python
import numpy as np

arr = np.array([[10, 20, 30],
                [40, 50, 60]])

# First row (index 0)
print("First row:", arr[0])        # [10 20 30]

# Second row (index 1)
print("Second row:", arr[1])       # [40 50 60]

# First row, first element → row 0, column 0
print("First row element:", arr[0, 0])   # 10

# Second row, first element → row 1, column 0
print("Second row element:", arr[1, 0])  # 40
```

> 💡 Remember: rows and columns both start at **0** in NumPy. So `arr[1, 2]` means row index 1, column index 2.

---

## 11. Array Manipulation – Reshape

`.reshape()` changes the shape of an array without changing its data. The total number of elements must stay the same.

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])
print("Original (1D):", arr.shape)  # (6,)

# Reshape to 2 rows × 3 columns
reshaped = arr.reshape(2, 3)
print("Reshaped (2D):\n", reshaped)
print("New shape:", reshaped.shape)  # (2, 3)
```

**Output:**
```
Reshaped (2D):
 [[1 2 3]
  [4 5 6]]
New shape: (2, 3)
```

> 💡 6 elements → can reshape to `(2, 3)` or `(3, 2)` or `(1, 6)` but NOT `(2, 4)` because 2×4 = 8 ≠ 6.

---

## 12. Concatenation in NumPy

Concatenation joins arrays together along a specified axis.

### Using `np.concatenate()`

```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# 1D concatenation
result = np.concatenate([a, b])
print("Concatenated 1D:", result)  # [1 2 3 4 5 6]
```

---

### Append (pandas-style)

```python
import pandas as pd

df1 = pd.DataFrame({'name': ['Alice', 'Bob'], 'score': [88, 72]})
df2 = pd.DataFrame({'name': ['Carol'], 'score': [95]})

# Append df2 to df1 (use pd.concat in modern pandas)
combined = pd.concat([df1, df2], ignore_index=True)
print(combined)
```

**Output:**
```
    name  score
0  Alice     88
1    Bob     72
2  Carol     95
```

> 💡 In newer versions of pandas (1.4+), `df.append()` is deprecated — use `pd.concat()` instead.

---

### Append to a 2D Array

```python
import numpy as np

arr_2d = np.array([[1, 2, 3],
                   [4, 5, 6]])

new_row = np.array([[7, 8, 9]])

# Append a new row (axis=0 means row-wise)
result = np.concatenate([arr_2d, new_row], axis=0)
print("Appended 2D array:\n", result)
```

**Output:**
```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```

> 💡 `axis=0` stacks rows vertically. `axis=1` stacks columns horizontally.

---

## 13. Broadcasting in NumPy

Broadcasting allows NumPy to perform operations on arrays of **different shapes** by automatically expanding the smaller array to match the larger one — without copying data.

```python
import numpy as np

arr = np.array([[1, 2, 3],
                [4, 5, 6]])

scalar = 10

# Scalar is broadcast to every element
print("Array + Scalar:\n", arr + scalar)

# 1D array broadcast across all rows
row = np.array([1, 0, 1])
print("\nArray + Row:\n", arr + row)
```

**Output:**
```
Array + Scalar:
 [[11 12 13]
  [14 15 16]]

Array + Row:
 [[2 2 4]
  [5 5 7]]
```

> 💡 Broadcasting rules: NumPy compares shapes from the **right**. Dimensions must either be equal or one of them must be `1`. This avoids writing explicit loops and makes code faster and cleaner.



*📍 Vee | Software Engineering Graduate | Murang'a University of Technology*  
*🐙 GitHub: [cybertech-lakewood](https://github.com/cybertech-lakewood)*  
*💼 LinkedIn: [viena-ouma](https://linkedin.com/in/viena-ouma)*
