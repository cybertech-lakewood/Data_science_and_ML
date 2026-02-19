# Week 2 Lab – Python Data Structures

## Lab Title
*Data Structures in Python: Lists, Tuples, Dictionaries & Sets*

---

## Objective
To understand and practise working with Python's core built-in data structures — Lists, Tuples, Dictionaries, and Sets — by applying their key methods and operations in a hands-on coding environment (Google Colab).

---

## Tools Used
| Tool | Purpose |
|---|---|
| Python 3 | Programming language |
| Google Colab | 


---

## Step-by-Step Process

### 1. Lists
A list is an ordered, mutable collection. The following methods were practised:

| Method | Description | Example Output |
|---|---|---|
| append(6) | Adds element to end | [1, 2, 3, 4, 5, 6] |
| extend([7,8,9]) | Adds multiple elements | [1, 2, 3, 4, 5, 6, 7, 8, 9] |
| insert(2, 10) | Inserts at given index | [1, 2, 10, 3, 4, 5, 6, 7, 8, 9] |
| remove(3) | Removes first occurrence | [1, 2, 10, 4, 5, 6, 7, 8, 9] |
| pop(3) | Removes & returns element at index | Returns 4 |
| index(5) | Returns index of element | 3 |
| count(10) | Counts occurrences | 1 |
| sort() | Sorts in ascending order | [1, 2, 5, 6, 7, 8, 9, 10] |
| reverse() | Reverses list in-place | [10, 9, 8, 7, 6, 5, 2, 1] |
| sorted() | Returns new sorted list | [1, 2, 2, 3, 4, 5, 6, 7, 8, 9, 10] |

### 2. Tuples
A *tuple* is an ordered, *immutable* collection. Methods practised:

| Method | Description | Example Output |
|---|---|---|
| count(3) | Counts occurrences of element | 1 |
| index(4) | Returns index of element | 3 |
| Indexing [1] | Access element by index | 2 |

### 3. Dictionaries
A *dictionary* stores key-value pairs. Methods practised:

| Method | Description |
|---|---|
| get('age') | Safely retrieves value by key |
| dict['age'] | Direct key indexing |
| items() | Returns all key-value pairs |
| keys() | Returns all keys |
| values() | Returns all values |
| update({...}) | Updates/adds key-value pairs |

*Example dictionary used:*
python
my_dict = {"name": "Simon", "age": 21, "city": "Nairobi"}


A multi-record dictionary was also created using dict() with a list of tuples:
python
my_dictionary = dict([
    ('name', ['Markie', 'Eunice', 'Molenza']),
    ('age', [22, 20, 26]),
    ('city', ['Nairobi', 'Nakuru', 'Kisumu'])
])


### 4. Sets
A *set* is an unordered collection of unique elements. Methods practised:

| Method | Description |
|---|---|
| add(6) | Adds one element |
| update({7,8,9}) | Adds multiple elements |
| remove(3) | Removes element (raises error if missing) |
| discard(5) | Removes element (no error if missing) |
| pop() | Removes and returns a random element |
| clear() | Empties the set |
| union() / \| | All elements from both sets |
| intersection() / & | Common elements only |
| difference() | Elements in one set but not the other |
| symmetric_difference() | Elements in either set but not both |

*Set operations example:*
python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

set1.union(set2)               # {1, 2, 3, 4, 5}
set1.intersection(set2)        # {3}
set1.difference(set2)          # {1, 2}
set1.symmetric_difference(set2) # {1, 2, 4, 5}


---

## Commands Executed (Key Code Snippets)

python
# --- LISTS ---
my_list = [1, 2, 3, 4, 5]
my_list.append(6)
my_list.extend([7, 8, 9])
my_list.insert(2, 10)
my_list.remove(3)
popped_element = my_list.pop(3)
my_list.sort()
my_list.reverse()

# --- TUPLES ---
my_tuple = (1, 2, 3, 4, 5)
my_tuple.count(3)
my_tuple.index(4)

# --- DICTIONARIES ---
my_dict = {"name": "Simon", "age": 21, "city": "Nairobi"}
my_dict.get('age')
my_dict.update({'age': 25, 'gender': 'Male'})

# --- SETS ---
my_set = {1, 2, 3, 4, 5}
my_set.add(6)
my_set.update({7, 8, 9})
my_set.remove(3)
my_set.discard(5)
set1.union(set2)
set1.intersection(set2)
set1.difference(set2)
set1.symmetric_difference(set2)


---

## Screenshots of Results

> (Screenshots from Google Colab showing cell outputs are included in the /screenshots folder or can be viewed by opening the .ipynb file directly on GitHub.)

Key outputs observed:
- [1, 2, 3, 4, 5, 6] → after append(6)
- [1, 2, 5, 6, 7, 8, 9, 10] → after sort()
- dict_items([('name', 'Simon'), ('age', 21), ('city', 'Nairobi')]) → .items()
- {1, 2, 3, 4, 5} → union() of {1,2,3} and {3,4,5}
- {3} → intersection() of {1,2,3} and {3,4,5}

---

## Key Observations / Lessons Learned

1. *Lists are versatile* – they support ordering, indexing, and a rich set of methods for data manipulation.
2. *Tuples are immutable* – once created they cannot be changed, making them ideal for fixed data like coordinates or configuration values.
3. *Dictionaries enable structured data storage* – using key-value pairs is very similar to how data is stored in tables or JSON, which is fundamental in data science.
4. *Sets automatically handle duplicates* – perfect for deduplication tasks and mathematical set operations (union, intersection, difference).
5. *sort() modifies in place while sorted() returns a new list* – this distinction matters when you need to preserve the original data.
6. *remove() vs discard() in sets* – remove() raises a KeyError if the element doesn't exist, while discard() does nothing. Always prefer discard() when unsure.
7. *Dictionaries can hold lists as values* – this makes them useful for representing small datasets, similar to a table with columns.

---


