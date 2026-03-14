# Week 5 – Day 2: NumPy Advanced Topics & Matplotlib Visualizations

> **Learning Journey** | Python for Data Science | cybertech-lakewood

---

## 📋 Table of Contents

1. [Random Number Generation in NumPy](#1-random-number-generation-in-numpy)
2. [Linear Algebra in NumPy](#2-linear-algebra-in-numpy)
3. [Deleting Elements in Arrays](#3-deleting-elements-in-arrays)
4. [Statistical Functions](#4-statistical-functions)
5. [Matplotlib – Types of Visualizations](#5-matplotlib--types-of-visualizations)
6. [Qualitative Visualizations](#6-qualitative-visualizations)
7. [Quantitative Visualizations](#7-quantitative-visualizations)

---

## 1. Random Number Generation in NumPy

NumPy's `random` module lets you generate random numbers for simulations, testing, and sampling.

### Generating Random Integers

```python
import numpy as np

# Generate a single random integer between 0 and 9
print(np.random.randint(0, 10))

# Generate an array of 5 random integers between 1 and 100
arr = np.random.randint(1, 100, size=5)
print("Random integers:", arr)
```

**Example Output:**
```
7
Random integers: [23 57  4 89 12]
```

> 💡 `np.random.randint(low, high, size)` generates integers from `low` up to (but not including) `high`. Every run gives different values unless you set a seed with `np.random.seed()`.

---

### Reshaping and Resizing

```python
import numpy as np

# Generate 12 random integers and reshape into a 3×4 matrix
arr = np.random.randint(1, 50, size=12).reshape(3, 4)
print("Reshaped random array:\n", arr)

# Resize — modifies shape in place (repeats data if needed)
arr_resized = np.resize(arr, (2, 6))
print("\nResized array:\n", arr_resized)
```

> 💡 `.reshape()` returns a new view with a different shape. `.resize()` can change the total number of elements — it fills extra spots by repeating the data from the beginning.

---

### `np.random.randn()` – Standard Normal Distribution

```python
import numpy as np

# Generate a 3×3 array of random floats from a standard normal distribution
arr = np.random.randn(3, 3)
print("randn array:\n", arr)
```

**Example Output:**
```
[[ 0.47  -1.23   0.89]
 [ 0.02   1.56  -0.34]
 [-0.78   0.11   2.01]]
```

> 💡 `randn` draws values from a normal (bell-curve) distribution with mean = 0 and standard deviation = 1. Useful for simulating real-world data like heights, test scores, or noise.

---

### `np.random.choice()`

```python
import numpy as np

items = ['apple', 'banana', 'cherry', 'date']

# Pick 1 random item
print(np.random.choice(items))

# Pick 3 random items with replacement (same item can be picked again)
print(np.random.choice(items, size=3, replace=True))

# Pick 3 random items WITHOUT replacement (each item appears once)
print(np.random.choice(items, size=3, replace=False))
```

> 💡 `.choice()` is like drawing from a bag. `replace=True` puts the item back before the next draw; `replace=False` doesn't — so no duplicates.

---

## 2. Linear Algebra in NumPy

NumPy's `linalg` module makes matrix operations fast and intuitive.

```python
import numpy as np

A = np.array([[1, 2],
              [3, 4]])

B = np.array([[5, 6],
              [7, 8]])
```

### Matrix Addition

```python
print("Addition:\n", A + B)
```
```
[[ 6  8]
 [10 12]]
```
> 💡 Corresponding elements are added together. Same rule as element-wise operations.

---

### Matrix Subtraction

```python
print("Subtraction:\n", A - B)
```
```
[[-4 -4]
 [-4 -4]]
```

---

### Matrix Multiplication – Overview

There are three different ways to "multiply" matrices in NumPy, and they produce very different results:

| Method | Operator / Function | Description |
|--------|---------------------|-------------|
| Element-wise | `A * B` | Multiply matching positions |
| Column-wise (dot product) | `np.dot(A, B)` | Row × Column sum |
| Standard matrix multiplication | `A @ B` | Same as dot product (cleaner syntax) |

---

### Normal (Element-wise) Multiplication

```python
print("Element-wise multiplication:\n", A * B)
```
```
[[ 5 12]
 [21 32]]
```
> 💡 Each element in A is multiplied by the element in the same position in B. This is NOT the same as matrix multiplication in linear algebra.

---

### Matrix Multiplication – Column-wise (dot product)

```python
print("Column-wise (np.dot):\n", np.dot(A, B))
```
```
[[19 22]
 [43 50]]
```
> 💡 `np.dot()` computes the sum of products of rows × columns. For example, row 1 of A `[1, 2]` dot column 1 of B `[5, 7]` = (1×5) + (2×7) = 19.

---

### Standard Matrix Multiplication

```python
print("Standard matrix multiplication (@ operator):\n", A @ B)
```
```
[[19 22]
 [43 50]]
```
> 💡 The `@` operator is the modern, preferred syntax for matrix multiplication. It produces the same result as `np.dot()` but is more readable.

---

### Transpose of a Matrix

```python
print("Transpose of A:\n", A.T)
```
```
[[1 3]
 [2 4]]
```
> 💡 Transposing flips the matrix — rows become columns and columns become rows. A shape `(2, 3)` matrix becomes `(3, 2)` after transposing.

---

### Inverse of a Matrix

```python
inv_A = np.linalg.inv(A)
print("Inverse of A:\n", inv_A)
```
```
[[-2.   1. ]
 [ 1.5 -0.5]]
```
> 💡 The inverse of matrix A (written A⁻¹) is the matrix that, when multiplied with A, gives the identity matrix. Only square matrices with a non-zero determinant have an inverse.

---

### Identity Matrix

```python
I = np.eye(3)
print("3×3 Identity Matrix:\n", I)
```
```
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```
> 💡 The identity matrix has 1s on the diagonal and 0s everywhere else. Multiplying any matrix by the identity matrix returns the original matrix — it's the matrix equivalent of multiplying by 1.

---

### Determinant of a Matrix

```python
det = np.linalg.det(A)
print("Determinant of A:", round(det, 2))
```
```
Determinant of A: -2.0
```
> 💡 The determinant is a single number that tells you if a matrix is invertible. If the determinant is 0, the matrix has no inverse (it's called singular). For `[[1,2],[3,4]]`: det = (1×4) − (2×3) = −2.

---

## 3. Deleting Elements in Arrays

Use `np.delete()` to remove elements, rows, or columns from an array.

```python
import numpy as np

arr_1d = np.array([10, 20, 30, 40, 50])

# Delete element at index 2 (value 30)
result = np.delete(arr_1d, 2)
print("After deleting index 2:", result)  # [10 20 40 50]

# 2D array — delete a row or column
arr_2d = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])

# Delete row at index 1 (axis=0 means rows)
no_row = np.delete(arr_2d, 1, axis=0)
print("\nDelete row 1:\n", no_row)

# Delete column at index 0 (axis=1 means columns)
no_col = np.delete(arr_2d, 0, axis=1)
print("\nDelete column 0:\n", no_col)
```

**Output:**
```
After deleting index 2: [10 20 40 50]

Delete row 1:
 [[1 2 3]
  [7 8 9]]

Delete column 0:
 [[2 3]
  [5 6]
  [8 9]]
```

> 💡 `np.delete()` always returns a **new** array — the original is not changed. Use `axis=0` for rows and `axis=1` for columns.

---

## 4. Statistical Functions

### Mean

```python
import numpy as np

data = np.array([10, 20, 30, 40, 50])
print("Mean:", np.mean(data))  # 30.0
```
> 💡 The mean is the sum of all values divided by the count. It represents the average.

---

### Mode (using SciPy)

NumPy does not have a built-in mode function — we use SciPy instead.

```python
from scipy import stats
import numpy as np

data = np.array([1, 2, 2, 3, 3, 3, 4])
mode_result = stats.mode(data, keepdims=True)

print("Mode:", mode_result.mode[0])       # 3
print("Count:", mode_result.count[0])     # 3
```
> 💡 The mode is the most frequently occurring value. SciPy's `stats.mode()` returns both the mode value and how many times it appears. `keepdims=True` avoids a deprecation warning in newer SciPy versions.

---

### Median

```python
import numpy as np

data = np.array([10, 20, 30, 40, 50])
print("Median:", np.median(data))  # 30.0

# With even number of elements — average of the two middle values
data_even = np.array([10, 20, 30, 40])
print("Median (even):", np.median(data_even))  # 25.0
```
> 💡 The median is the middle value when data is sorted. It's less affected by extreme values (outliers) than the mean.

---

### Standard Deviation

```python
import numpy as np

data = np.array([10, 20, 30, 40, 50])
print("Standard Deviation:", np.std(data))  # 14.14
```
> 💡 Standard deviation measures how spread out values are from the mean. A low std means values cluster tightly around the mean; a high std means they are more spread out.

---

## 5. Matplotlib – Types of Visualizations

Matplotlib is Python's core plotting library. Different chart types suit different kinds of data:

| Visualization | Type | Best Used For |
|---------------|------|---------------|
| Bar Chart | Qualitative | Comparing categories |
| Pie Chart | Qualitative | Showing proportions of a whole |
| Heatmap | Quantitative | Showing correlations or matrix data |
| Line Plot | Quantitative | Trends over time or sequence |
| Scatter Plot | Quantitative | Relationships between two variables |
| Box Plot | Quantitative | Spread, median, and outliers |
| Violin Plot | Quantitative | Distribution shape + summary stats |
| Histogram | Quantitative | Frequency distribution of one variable |

---

## 6. Qualitative Visualizations

Qualitative (categorical) data describes categories, groups, or labels — not measurements.

### Bar Chart – Iris Dataset

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

# Load the Iris dataset
iris = sns.load_dataset('iris')

# Count how many flowers belong to each species
species_counts = iris['species'].value_counts()

# Plot the bar chart
plt.figure(figsize=(7, 5))
plt.bar(species_counts.index, species_counts.values, color=['steelblue', 'salmon', 'mediumseagreen'])
plt.title('Count of Each Iris Species')
plt.xlabel('Species')
plt.ylabel('Count')
plt.tight_layout()
plt.show()
```

**Interpretation:**
The bar chart shows that the Iris dataset is **perfectly balanced** — each of the three species (setosa, versicolor, and virginica) has exactly 50 samples. This balance is important in machine learning because it means a model won't be biased towards any one class.

---

### Pie Chart – Iris Species

```python
import matplotlib.pyplot as plt
import seaborn as sns

iris = sns.load_dataset('iris')
species_counts = iris['species'].value_counts()

plt.figure(figsize=(6, 6))
plt.pie(
    species_counts.values,
    labels=species_counts.index,
    autopct='%1.1f%%',
    colors=['steelblue', 'salmon', 'mediumseagreen'],
    startangle=90
)
plt.title('Proportion of Iris Species')
plt.tight_layout()
plt.show()
```

**Interpretation:**
Each species makes up exactly **33.3%** of the dataset. The pie chart visually confirms the equal distribution. `autopct='%1.1f%%'` automatically calculates and displays the percentage for each slice.

---

## 7. Quantitative Visualizations

Quantitative data involves measurable numerical values — lengths, weights, temperatures, etc.

### Heatmap – Correlation Matrix

**What is a heatmap?**
A heatmap uses colour intensity to represent values in a matrix. In data science, it is commonly used to display **correlation matrices** — showing how strongly pairs of numerical variables relate to each other. Values range from -1 (strong negative correlation) to +1 (strong positive correlation).

```python
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# Step 1: Load the dataset
iris = sns.load_dataset('iris')

# Step 2: Find the correlation matrix (numeric columns only)
corr_matrix = iris.drop(columns=['species']).corr()

# Step 3: Set up the plot and add annotations
fig, ax = plt.subplots(figsize=(8, 6))
heatmap = ax.imshow(corr_matrix, cmap='coolwarm', vmin=-1, vmax=1)

# Step 4: Add colorbar
plt.colorbar(heatmap, ax=ax, label='Correlation Coefficient')

# Step 5: Set labels
ax.set_xticks(range(len(corr_matrix.columns)))
ax.set_yticks(range(len(corr_matrix.columns)))
ax.set_xticklabels(corr_matrix.columns, rotation=45, ha='right')
ax.set_yticklabels(corr_matrix.columns)

# Step 6: Add annotations (show correlation value inside each cell)
for i in range(len(corr_matrix)):
    for j in range(len(corr_matrix.columns)):
        ax.text(j, i, f"{corr_matrix.iloc[i, j]:.2f}",
                ha='center', va='center', color='black', fontsize=10)

# Step 7: Add title and show plot
ax.set_title('Iris Dataset – Correlation Heatmap', fontsize=14, pad=15)
plt.tight_layout()
plt.show()
```

**Interpretation:**
- `petal_length` and `petal_width` have a very high correlation (~0.96), meaning longer petals tend to also be wider.
- `sepal_length` correlates moderately with petal measurements.
- Warm colours (red) indicate strong positive correlation; cool colours (blue) indicate negative correlation.

---

### Line Plot – Sepal Length

```python
import matplotlib.pyplot as plt
import seaborn as sns

iris = sns.load_dataset('iris')

plt.figure(figsize=(10, 5))
plt.plot(iris.index, iris['sepal_length'], color='steelblue', linewidth=1, label='Sepal Length')
plt.title('Sepal Length Across All Iris Samples')
plt.xlabel('Sample Index')
plt.ylabel('Sepal Length (cm)')
plt.legend()
plt.tight_layout()
plt.show()
```

**Interpretation:**
The line plot reveals the variation in sepal length across all 150 samples. Because the dataset is ordered by species (setosa 0–49, versicolor 50–99, virginica 100–149), you can observe a general **upward trend** in sepal length as you move from setosa to virginica — with setosa having the smallest sepal lengths on average.

---

### Scatter Plot – Sepal Length vs Sepal Width

```python
import matplotlib.pyplot as plt
import seaborn as sns

iris = sns.load_dataset('iris')

colors = {'setosa': 'steelblue', 'versicolor': 'salmon', 'virginica': 'mediumseagreen'}

plt.figure(figsize=(8, 6))
for species, group in iris.groupby('species'):
    plt.scatter(group['sepal_length'], group['sepal_width'],
                label=species, color=colors[species], alpha=0.7)

plt.title('Sepal Length vs Sepal Width by Species')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Sepal Width (cm)')
plt.legend()
plt.tight_layout()
plt.show()
```

**Interpretation:**
The scatter plot shows that **setosa** (blue) is clearly separated from the other two species — it has smaller sepal lengths but relatively wider sepals. Versicolor and virginica overlap more, making them harder to distinguish by sepal dimensions alone.

---

### Box Plot – Outliers

```python
import matplotlib.pyplot as plt
import seaborn as sns

iris = sns.load_dataset('iris')

plt.figure(figsize=(8, 6))
iris.boxplot(column='sepal_length', by='species', grid=False,
             boxprops=dict(color='steelblue'),
             medianprops=dict(color='red', linewidth=2))
plt.title('Sepal Length Distribution by Species')
plt.suptitle('')   # Removes the default "Boxplot grouped by" title
plt.xlabel('Species')
plt.ylabel('Sepal Length (cm)')
plt.tight_layout()
plt.show()
```

**How to read the box plot:**
- The **box** spans from the 25th percentile (Q1) to the 75th percentile (Q3) — this is the Interquartile Range (IQR).
- The **red line** inside the box is the median.
- The **whiskers** extend to the smallest/largest values within 1.5×IQR.
- Points **outside the whiskers** are outliers.

**Interpretation:**
Virginica has the largest sepal lengths with some variation. Setosa has the smallest and tightest distribution. Any dots outside the whiskers represent unusual measurements worth investigating.

---

### Violin Plot

```python
import matplotlib.pyplot as plt
import seaborn as sns

iris = sns.load_dataset('iris')

plt.figure(figsize=(9, 6))
sns.violinplot(data=iris, x='species', y='sepal_length',
               palette=['steelblue', 'salmon', 'mediumseagreen'])
plt.title('Violin Plot of Sepal Length by Species')
plt.xlabel('Species')
plt.ylabel('Sepal Length (cm)')
plt.tight_layout()
plt.show()
```

**Interpretation:**
The violin plot combines a box plot with a **kernel density estimate** — the wider the violin, the more data points cluster at that value. Setosa's violin is short and compact (low variation), while virginica's is taller and wider at the top, showing larger and more varied sepal lengths. This gives more information than a box plot alone.

---

### Histogram – Sepal Length

```python
import matplotlib.pyplot as plt
import seaborn as sns

iris = sns.load_dataset('iris')

plt.figure(figsize=(8, 5))
plt.hist(iris['sepal_length'], bins=20, color='steelblue', edgecolor='white')
plt.title('Histogram of Sepal Length')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Frequency')
plt.tight_layout()
plt.show()

# Overlapping histograms by species
plt.figure(figsize=(9, 5))
for species, group in iris.groupby('species'):
    plt.hist(group['sepal_length'], bins=15, alpha=0.6, label=species)
plt.title('Sepal Length Distribution by Species')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Frequency')
plt.legend()
plt.tight_layout()
plt.show()
```

**Interpretation:**
The histogram shows the **frequency distribution** of sepal lengths across all 150 samples. Most values fall between 5.0 cm and 7.0 cm, with the distribution roughly bell-shaped. The overlapping histogram by species reveals that setosa has a narrower, lower distribution while virginica extends further to the right — confirming it has longer sepals on average.

---

## 🗂️ Summary Table

| Topic | Key Function / Concept |
|-------|------------------------|
| Random integers | `np.random.randint(low, high, size)` |
| Reshape random array | `.reshape(rows, cols)` |
| Normal distribution | `np.random.randn(rows, cols)` |
| Random choice | `np.random.choice(arr, size, replace)` |
| Matrix addition/subtraction | `A + B`, `A - B` |
| Element-wise multiplication | `A * B` |
| Dot product / column-wise | `np.dot(A, B)` |
| Standard matrix multiply | `A @ B` |
| Transpose | `A.T` |
| Inverse | `np.linalg.inv(A)` |
| Identity matrix | `np.eye(n)` |
| Determinant | `np.linalg.det(A)` |
| Delete elements | `np.delete(arr, index, axis)` |
| Mean | `np.mean()` |
| Mode | `scipy.stats.mode()` |
| Median | `np.median()` |
| Standard deviation | `np.std()` |
| Bar chart | `plt.bar()` |
| Pie chart | `plt.pie()` |
| Heatmap | `ax.imshow()` + `plt.colorbar()` |
| Line plot | `plt.plot()` |
| Scatter plot | `plt.scatter()` |
| Box plot | `df.boxplot()` |
| Violin plot | `sns.violinplot()` |
| Histogram | `plt.hist()` |


*Vee | Software Engineering Graduate | Murang'a University of Technology*  
*GitHub: [cybertech-lakewood](https://github.com/cybertech-lakewood)*  
*LinkedIn: [viena-ouma](https://linkedin.com/in/viena-ouma)*
