# Python Strings and Control Flows Guide

A comprehensive guide to working with strings in Python.

## Table of Contents

- [Strings](#strings)
  - [String Methods](#string-methods)
  - [String Checking Methods](#string-checking-methods)


---

## Strings

Strings are sequences of characters in Python. They can be manipulated using various built-in methods.

### Creating Strings

```python
name_ = "ParoCyber LLC"
print(name_)  # Output: ParoCyber LLC
```

### String Methods

#### upper()
Converts all characters in a string to uppercase.

```python
name_ = "ParoCyber LLC"
name_ = name_.upper()
print(name_)  # Output: PAROCYBER LLC
```

#### lower()
Converts all characters in a string to lowercase.

```python
name_ = "ParoCyber LLC"
name_ = name_.lower()
print(name_)  # Output: parocyber llc
```

#### title()
Converts the first character of each word to uppercase.

```python
name_ = "ParoCyber LLC"
name_ = name_.title()
print(name_)  # Output: Parocyber Llc
```

#### capitalize()
Converts the first character of the string to uppercase and the rest to lowercase.

```python
name_ = "ParoCyber LLC"
name_ = name_.capitalize()
print(name_)  # Output: Parocyber llc
```

### String Checking Methods

These methods return boolean values (True or False) to check properties of a string.

#### isalpha()
Checks whether all characters in the string are alphabets. Returns False if there are spaces, numbers, or special characters.

```python
name_ = "ParoCyber LLC"
result = name_.isalpha()
print(result)  # Output: False (contains space)

name2 = "ParoCyberLLC"
result = name2.isalpha()
print(result)  # Output: True
```

#### isdigit()
Checks whether all characters in the string are digits (numbers).

```python
text = "12345"
result = text.isdigit()
print(result)  # Output: True

text = "123A45"
result = text.isdigit()
print(result)  # Output: False
```

#### islower()
Checks whether all cased characters in the string are lowercase.

```python
name_ = "parocyber llc"
result = name_.islower()
print(result)  # Output: True

name_ = "ParoCyber LLC"
result = name_.islower()
print(result)  # Output: False
```

#### isupper()
Checks whether all cased characters in the string are uppercase.

```python
name_ = "PAROCYBER LLC"
result = name_.isupper()
print(result)  # Output: True

name_ = "ParoCyber LLC"
result = name_.isupper()
print(result)  # Output: False
```


#### split()
Splits a string into a list of substrings based on a specified delimiter (default is space).

```python
car = "I love my new BMW car"
result = car.split(" ")
print(result)  # Output: ['I', 'love', 'my', 'new', 'BMW', 'car']

# Split by different delimiter
text = "apple,banana,orange"
result = text.split(",")
print(result)  # Output: ['apple', 'banana', 'orange']
```

#### join()
Combines list elements into a single string with a specified separator.

```python
car = "I love my new BMW car"
words = car.split(" ")
result = "_".join(words)
print(result)  # Output: I_love_my_new_BMW_car

# Using different separator
result = "-".join(words)
print(result)  # Output: I-love-my-new-BMW-car
```

#### replace()
Replaces all occurrences of a substring with another substring.

```python
car = "I love my new BMW car"
new_car = car.replace("BMW", "Audi")
print(new_car)  # Output: I love my new Audi car

```


#### startswith()
Checks if a string starts with a specified prefix.

```python
Cars = "Audi"
Cars.startswith("A")  # Output: True

```

#### endswith()
Checks if a string ends with a specified suffix.

```python
text = "Hello World"
result = text.endswith("World")
print(result)  # Output: True

Cars = "Audi"
Cars.endswith("A")  # Output: False
```




