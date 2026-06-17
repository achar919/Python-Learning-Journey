# What Is an Object in Python?

## Core Idea

In Python, **everything is an object**.

When you write:

```python
x = 10
```

Python does not store a raw `10`. It creates an **object** and `x` refers to that object.

---

## Every Object Has 3 Properties

| Property | Meaning                   | Check Using |
| -------- | ------------------------- | ----------- |
| Type     | What kind of object it is | `type(x)`   |
| Value    | The data it holds         | `print(x)`  |
| Identity | Unique memory identifier  | `id(x)`     |

---

## Example

```python
x = 42

print(type(x))
print(x)
print(id(x))
```

### Output

```python
<class 'int'>
42
4392513824
```

**Explanation**

* Type → `int`
* Value → `42`
* Identity → Unique memory ID

---

## Memory View

```text
 STACK                    HEAP

┌─────┐
│  x  │ ───────────────▶ Object
└─────┘                  Type: int
(variable)               Value: 10
                          ID: 4392513792
```

* Variable `x` stores a reference.
* The actual object lives in memory (heap).

---

## Type

Type tells Python what kind of object it is.

```python
x = 10
print(type(x))
```

Output:

```python
<class 'int'>
```

Examples:

```python
10          # int
3.14        # float
"hello"     # str
True        # bool
[1, 2, 3]   # list
```

---

## Value

Value is the actual data stored in the object.

```python
x = 42
print(x)
```

Output:

```python
42
```

---

## Identity

Identity is a unique ID for the object.

```python
x = 42
print(id(x))
```

Output:

```python
4392513824
```

> The number will be different on your computer.

---

## Value Comparison (`==`)

`==` checks whether two objects have the same value.

```python
a = 10
b = 10

print(a == b)
```

Output:

```python
True
```

Because both contain the value `10`.

---

## Identity Comparison (`is`)

`is` checks whether two variables refer to the same object.

```python
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
print(a is b)
```

Output:

```python
True
False
```

### Why?

```python
a == b
```

Checks values:

```python
[1, 2, 3] == [1, 2, 3]
```

Result:

```python
True
```

```python
a is b
```

Checks identities.

These are two different list objects in memory.

Result:

```python
False
```

---

## Why Objects Matter

Understanding objects helps explain:

* Variables
* Memory
* `==` vs `is`
* Function arguments
* Mutable vs immutable objects
* Many Python errors

---

* `is` compares identities.
* Variables store references to objects, not the actual objects themselves.
