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
* `is` compares identities.
* Variables store references to objects, not the actual objects themselves.

# Dynamic Typing — Variables Are Not Locked to a Type

Because variables are name tags (not boxes), a variable can point to any type of object — and you can change it anytime:

```python
x = 10
print(type(x))   # <class 'int'>

x = "hello"
print(type(x))   # <class 'str'>

x = 3.14
print(type(x))   # <class 'float'>

x = True
print(type(x))   # <class 'bool'>
```

Python does not complain. The variable x is just a name tag — first it pointed to an integer object, then a string object, then a float, then a boolean. The name tag moved. That is dynamic typing.

In the IT company — it is like the receptionist updating the register. "x" was pointing to a developer on the 4th floor. Now "x" points to a designer on the 2nd floor. The register (stack) just updated the arrow. The receptionist does not care what type of employee it is.

Dynamic typing makes Python fast to write and experiment with — no type declarations, no restrictions.

But it also means Python will not warn you if a variable changes type unexpectedly:

```python
count = 10
count = input("Enter count: ")  # Now count is a string, not an int
print(count + 1)                # TypeError!
```

The fix is always the same — be aware of your types. Use `type()` to check when debugging.

# Integer Caching

Python optimizes small integers. Integers from -5 to 256 are cached — Python creates them once at startup and reuses them.

```python
a = 100
b = 100
print(a is b)   # True — same cached object

a = 1000
b = 1000
print(a is b)   # may be False — not cached, separate objects
```

## How This Actually Works

When CPython starts — before your code even runs — it pre-creates 262 integer objects in the heap:

```text
-5, -4, -3, -2, -1, 0, 1, 2, 3, ... 254, 255, 256
```

These objects sit in the heap permanently. They are never destroyed during the program's lifetime.

When you write `a = 100`, Python checks: "Is 100 between -5 and 256?" Yes — so instead of creating a new object, it points `a` to the already existing `100` object. When you write `b = 100`, the same thing happens. Both variables point to the same pre-created object.

When you write `a = 1000`, Python checks: "Is 1000 between -5 and 256?" No — so it creates a new object. `b = 1000` creates another new object. Two separate objects, same value, different desks.
