# A Quick Binary Brush-Up

Binary is just another way to write numbers — using only two digits: 0 and 1. You already know the decimal system (base 10), where each position is a power of 10. Binary (base 2) works the same way, but each position is a power of 2:

```text
Position:    8    4    2    1     (powers of 2: 2³  2²  2¹  2⁰)
             ─    ─    ─    ─

Decimal 0:   0    0    0    0  →  0
Decimal 1:   0    0    0    1  →  1
Decimal 2:   0    0    1    0  →  2
Decimal 3:   0    0    1    1  →  2 + 1 = 3
Decimal 5:   0    1    0    1  →  4 + 1 = 5
Decimal 10:  1    0    1    0  →  8 + 2 = 10
```

That is all binary is — each slot is either ON (1) or OFF (0), and you add up the positions that are ON.

You can verify this in Python:

```python
print(bin(10))    # 0b1010
print(bin(255))   # 0b11111111
print(bin(1))     # 0b1
```

The `0b` prefix just means "this is a binary number."

## What About Text?

Text is also stored as 0s and 1s — but through an extra step. Every character has a number assigned to it (a character code). Python uses Unicode, where `'A'` is 65, `'B'` is 66, `'a'` is 97, and so on:

```python
print(ord('A'))         # 65
print(ord('a'))         # 97
print(bin(ord('A')))    # 0b1000001  — the binary of 65
```

So when Python stores the string `"Hi"` in the heap, it converts each character to its number, and each number to binary:

```text
'H' → 72  → 1001000
'i' → 105 → 1101001
```

Every piece of data — integers, floats, strings, booleans — is ultimately stored as a pattern of 0s and 1s in the heap. The type of the object tells Python how to interpret those 0s and 1s. The same 0s and 1s could mean a number, a letter, or a True/False — the type decides.

## The Problem with Decimals

Integers convert cleanly into binary — 10 is `1010`, 255 is `11111111`, no problem. But decimal numbers like `0.1` cannot be represented exactly in binary. That is not a Python bug — it is a fundamental limitation of how computers store data.

# The Full Picture — Every Data Type at a Glance


| Type     | What It Stores                | Mutable? | Example               | When You Use It                       |
| -------- | ----------------------------- | -------- | --------------------- | ------------------------------------- |
| int      | Whole numbers                 | No       | `10`, `-3`, `0`       | Counting, IDs, indexing               |
| float    | Decimal numbers               | No       | `3.14`, `-0.5`        | Prices, measurements, calculations    |
| bool     | True or False                 | No       | `True`, `False`       | Conditions, flags, comparisons        |
| NoneType | Absence of a value            | No       | `None`                | Default values, "nothing here"        |
| str      | Text (sequence of characters) | No       | `"hello"`, `"Python"` | Names, URLs, API data, file content   |
| list     | Items in sequence (any type)  | Yes      | `[1, 2, 3]`           | Shopping carts, user lists, logs      |
| tuple    | Ordered, fixed collection     | No       | `(12.97, 77.59)`      | Coordinates, config, RGB colors       |
| set      | Unique items (no order)       | Yes      | `{"Python", "SQL"}`   | Removing duplicates, permissions      |
| dict     | Key-value pairs               | Yes      | `{"name": "Dev"}`     | API responses, configs, database rows |

# Integers (`int`)

Integers are whole numbers without a decimal point.

```python
a = 10
b = -3
c = 0

print(type(a))  # <class 'int'>
```

## No Size Limit

Unlike many programming languages, Python integers can grow as large as available memory allows.

```python
big = 10 ** 100
print(big)
print(type(big))  # <class 'int'>
```

Python automatically allocates more memory when needed.

## Readable Large Numbers

Underscores can be used to improve readability. They are ignored by Python.

```python
population = 8_000_000_000
print(population)   # 8000000000

budget = 1_500_000.50
print(budget)       # 1500000.5
```

---

# Floats (`float`)

Floats represent numbers with decimal points.

```python
price = 99.99
temperature = -3.5

print(type(price))  # <class 'float'>
```

## Precision Problem

Floats are not always stored exactly because computers store them in binary.

```python
print(0.1 + 0.2)
```

Output:

```python
0.30000000000000004
```

This is normal behavior and occurs in most programming languages.

## Float Comparisons

```python
print(0.1 + 0.2 == 0.3)
```

Output:

```python
False
```

The comparison fails because of tiny precision differences.

## Handling Float Precision

### Using `round()`

```python
result = 0.1 + 0.2
print(round(result, 2))  # 0.3
```

### Using `Decimal`

```python
from decimal import Decimal

print(Decimal("0.1") + Decimal("0.2"))  # 0.3
```

`Decimal` performs exact decimal arithmetic and is commonly used in financial applications.

# Division Operators

Python has three division-related operators. Each behaves differently.

```python
print(10 / 3)    # 3.3333333333333335  (float division)
print(10 // 3)   # 3                   (floor division)
print(10 % 3)    # 1                   (modulus - remainder)
```

# Real-World Uses of These Operators

| Operator | Real-World Use Case                                           |
| -------- | ------------------------------------------------------------- |
| `/`      | Calculating averages, percentages                             |
| `//`     | Pagination: `total_items // items_per_page` gives total pages |
| `%`      | Checking even/odd: `number % 2 == 0`, cycling through options |

# Assignment Operators

Here is every assignment operator:

| Operator  | What It Does             | Equivalent To |
| --------- | ------------------------ | ------------- |
| `x = n`   | Assign value to variable | —             |
| `x += n`  | Add and assign           | `x = x + n`   |
| `x -= n`  | Subtract and assign      | `x = x - n`   |
| `x *= n`  | Multiply and assign      | `x = x * n`   |
| `x /= n`  | Divide and assign        | `x = x / n`   |
| `x //= n` | Floor divide and assign  | `x = x // n`  |
| `x %= n`  | Modulus and assign       | `x = x % n`   |
| `x **= n` | Exponent and assign      | `x = x ** n`  |

You will use `+=` constantly — in every loop counter, every running total, every accumulator pattern. When you see `i += 1` in Parts 12 and 13, you will know exactly what it means.

# abs() — Absolute Value

`abs()` returns the distance of a number from zero — always positive.

```python
print(abs(-10))    # 10
print(abs(10))     # 10
print(abs(-3.5))   # 3.5
print(abs(0))      # 0
```

You will see `abs()` used later in this part for comparing floats with a tolerance. It is also used in:

* Distance calculations: Difference between two values regardless of direction
* Error measurement: How far a prediction is from the actual value

# Built-In Numeric Functions — min, max, sum

Python provides three built-in functions that work on any collection of numbers:

```python
scores = [85, 92, 78, 95, 88]

print(min(scores))   # 78
print(max(scores))   # 95
print(sum(scores))   # 438
```

They also work with individual arguments:

```python
print(min(10, 3, 7))   # 3
print(max(10, 3, 7))   # 10
```

`sum()` only works on iterables (lists, tuples, etc.), not individual arguments.

A common pattern — calculating an average:

```python
scores = [85, 92, 78, 95, 88]
average = sum(scores) / len(scores)
print(f"Average: {average:.2f}")   # Average: 87.60
```

# Complete Numeric Operations Reference

Here is every arithmetic operator and numeric function covered in this part, in one place:

| Operation / Function | What It Does                                  | Example             | Result      |
| -------------------- | --------------------------------------------- | ------------------- | ----------- |
| `=`                  | Assign value to variable                      | `x = 10`            | `x` is `10` |
| `+`                  | Addition                                      | `7 + 3`             | `10`        |
| `-`                  | Subtraction                                   | `7 - 3`             | `4`         |
| `*`                  | Multiplication                                | `7 * 3`             | `21`        |
| `/`                  | True division (always returns float)          | `7 / 2`             | `3.5`       |
| `//`                 | Floor division (rounds down to int)           | `7 // 2`            | `3`         |
| `%`                  | Modulus (remainder)                           | `7 % 3`             | `1`         |
| `**`                 | Exponentiation                                | `2 ** 10`           | `1024`      |
| `abs(x)`             | Absolute value                                | `abs(-5)`           | `5`         |
| `round(x, n)`        | Round to n decimal places (banker's rounding) | `round(3.14159, 2)` | `3.14`      |
| `int(x)`             | Convert to integer (truncates toward zero)    | `int(3.9)`          | `3`         |
| `float(x)`           | Convert to float                              | `float(10)`         | `10.0`      |
| `pow(x, y)`          | Same as `x ** y`                              | `pow(2, 10)`        | `1024`      |
| `divmod(x, y)`       | Returns `(x // y, x % y)` as a tuple          | `divmod(17, 5)`     | `(3, 2)`    |
| `min(...)`           | Returns the smallest value                    | `min(3, 1, 7)`      | `1`         |
| `max(...)`           | Returns the largest value                     | `max(3, 1, 7)`      | `7`         |
| `sum(iterable)`      | Returns the total of all values               | `sum([1, 2, 3])`    | `6`         |
| `x += n`             | Add and assign (shorthand for `x = x + n`)    | `x = 10; x += 3`    | `13`        |
| `x -= n`             | Subtract and assign                           | `x = 10; x -= 3`    | `7`         |
| `x *= n`             | Multiply and assign                           | `x = 10; x *= 3`    | `30`        |
| `x /= n`             | Divide and assign                             | `x = 10; x /= 4`    | `2.5`       |
| `x //= n`            | Floor divide and assign                       | `x = 10; x //= 3`   | `3`         |
| `x %= n`             | Modulus and assign                            | `x = 10; x %= 3`    | `1`         |
| `x **= n`            | Exponent and assign                           | `x = 2; x **= 10`   | `1024`      |
