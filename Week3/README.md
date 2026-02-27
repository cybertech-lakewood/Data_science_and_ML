# Python Operators Guide

A comprehensive guide to understanding and using various operators in Python, including arithmetic, comparison, logical, assignment, bitwise, membership, and identity operators.

## Table of Contents

- [Arithmetic Operators](#arithmetic-operators)
- [Comparison Operators](#comparison-operators)
- [Logical Operators](#logical-operators)
- [Assignment Operators](#assignment-operators)
- [Bitwise Operators](#bitwise-operators)
- [Membership Operators](#membership-operators)
- [Identity Operators](#identity-operators)

## Arithmetic Operators

Arithmetic operators are used to perform mathematical operations on numeric values.

### Addition
```python
x = 10
y = 15
print(x + y)  # Output: 25
```

### Subtraction
```python
x = 10
y = 15
print(y - x)  # Output: 5
```

### Multiplication
```python
x = 10
y = 15
print(x * y)  # Output: 150
```

### Division
Returns a float result. Uses the forward slash (`/`).
```python
x = 300
y = 30
print(x / y)  # Output: 10.0
```

### Floor Division
Ignores the decimal part and returns only the whole number. Uses double forward slash (`//`).
```python
y = 300
x = 7
print(y // x)  # Output: 42
```

### Modulo
Returns the remainder after division. Uses the percent sign (`%`).
```python
y = 300
x = 7
print(y % x)  # Output: 6
```

### Exponentiation
Raises a number to the power of another. Uses double asterisk (`**`).
```python
y = 5
x = 6
print(y ** x)  # Output: 15625
```

## Comparison Operators

Comparison operators are used to compare two values and return a boolean result (True or False).

### Greater Than (`>`)
```python
x = 54
y = 32
print(x > y)  # Output: True
```

### Less Than (`<`)
```python
x = 54
y = 32
print(x < y)  # Output: False
```

### Equal To (`==`)
```python
x = 54
y = 32
print(x == y)  # Output: False
```

### Greater Than or Equal To (`>=`)
```python
x = 54
y = 32
print(x >= y)  # Output: True
```

### Less Than or Equal To (`<=`)
```python
x = 54
y = 32
print(x <= y)  # Output: False
```

### Not Equal To (`!=`)
```python
x = 54
y = 32
print(y != x)  # Output: True
```

## Logical Operators

Logical operators are used to combine conditional statements. Python has three logical operators: `and`, `or`, and `not`.

### AND Operator
Returns True if both conditions are True.
```python
x = 45
y = 32
print(x > 30 and y < 25)  # Output: False
print(x < 30 and y < 25)  # Output: False
```

### OR Operator
Returns True if at least one condition is True.
```python
x = 45
y = 32
print(x < 30 or y > 25)  # Output: True
```

### NOT Operator
Reverses the result; returns True if the condition is False.
```python
x = 45
print(not (x < 32))  # Output: True
```

## Assignment Operators

Assignment operators are used to assign values to variables. They can also perform operations while assigning.

### Basic Assignment (`=`)
```python
x = 55
print(x)  # Output: 55
```

### Add and Assign (`+=`)
```python
x = 55
x += 23
print(x)  # Output: 78
```

### Subtract and Assign (`-=`)
```python
x = 78
x -= 23
print(x)  # Output: 55
```

### Multiply and Assign (`*=`)
```python
x = 55
x *= 23
print(x)  # Output: 1265
```

### Divide and Assign (`/=`)
```python
x = 1265
x /= 23
print(x)  # Output: 55.0
```

### Floor Divide and Assign (`//=`)
```python
x = 55.0
x //= 23
print(x)  # Output: 2.0
```

### Exponentiate and Assign (`**=`)
```python
x = 2.0
x **= 23
print(x)  # Output: 8388608.0
```

## Bitwise Operators

Bitwise operators work on binary representations of integers. Python has six bitwise operators.

### AND (`&`)
Compares bits; returns 1 if both bits are 1.
```python
x = 10
y = 3
print(x & y)  # Output: 2

x = 10
y = 10
print(x & y)  # Output: 10
```

### OR (`|`)
Compares bits; returns 1 if at least one bit is 1.
```python
x = 10
y = 10
print(x | y)  # Output: 10
```

### XOR (`^`)
Returns 1 if bits differ, 0 if they're the same.
```python
x = 10
y = 10
print(x ^ y)  # Output: 0
```

### Bitwise NOT (`~`)
Inverts all bits (returns the two's complement).
```python
x = 10
print(~x)  # Output: -11
```

### Right Shift (`>>`)
Shifts bits to the right by the specified number of positions.
```python
x = 10
print(x >> 2)  # Output: 2
```

### Left Shift (`<<`)
Shifts bits to the left by the specified number of positions.
```python
x = 10
print(x << 2)   # Output: 40
print(x << 3)   # Output: 80
print(x << 5)   # Output: 320
```

### Understanding Binary
```python
print(bin(10))  # Output: 0b1010 (prefix 0b indicates binary)
print(bin(3))   # Output: 0b11
```

## Membership Operators

Membership operators are used to test if a value exists in a sequence or collection. Python has two membership operators: `in` and `not in`.

### Supported Sequences
- Strings
- Tuples
- Lists
- Dictionaries
- Sets

### IN Operator
Checks if a value exists in a sequence.
```python
a = [1, 2, 3, 4, 5]
print(2 in a)    # Output: True
print(8 in a)    # Output: False
```

### NOT IN Operator
Checks if a value does NOT exist in a sequence.
```python
a = [1, 2, 3, 4, 5]
print(4 not in a)   # Output: False
print(10 not in a)  # Output: True
```

## Identity Operators

Identity operators are used to compare if two objects are the same in memory, not just equal in value. Python has two identity operators: `is` and `is not`.

### IS Operator
Checks if two variables refer to the same object in memory.
```python
a = [1, 2, 3, 4, 5]
b = [1, 2, 3, 4, 5]
print(a is b)     # Output: False (different objects in memory)
```

### IS NOT Operator
Checks if two variables do NOT refer to the same object in memory.
```python
a = [1, 2, 3, 4, 5]
b = [1, 2, 3, 4, 5]
print(a is not b)  # Output: True (different objects in memory)
```

## Key Takeaways

- **Arithmetic operators** perform mathematical calculations
- **Comparison operators** evaluate conditions and return boolean values
- **Logical operators** combine multiple conditions
- **Assignment operators** assign values and can perform operations simultaneously
- **Bitwise operators** work directly with binary representations
- **Membership operators** check existence in collections
- **Identity operators** verify if objects are the same in memory, not just equal in value

---



