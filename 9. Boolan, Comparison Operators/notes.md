# The Boolean Type

* Most used type in all of programming — every decision a program makes depends on a boolean
* Only two possible values: `True` and `False`
* These are keywords in Python — you cannot use them as variable names

```python
print(True)
print(False)
print(type(True))   # <class 'bool'>
```

# Booleans Are Objects in the Heap

* Same rule from Parts 7-8: everything is an object
* `True` is an object stored in the heap
* The variable on the stack holds a reference (arrow) pointing to it

```python
x = True

print(type(x))    # <class 'bool'>
print(id(x))      # some memory address — this is the object's location in the heap
```

```text
STACK                    HEAP

┌──────────┐            ┌──────────────────┐
│ x  ──────│───────────▶│ type: bool       │
└──────────┘            │ value: True      │
                        │ id: 4345618736   │
                        └──────────────────┘
```

# The `bool()` Constructor

Explicitly convert any value to a boolean.

```python
print(bool(1))       # True
print(bool(0))       # False
print(bool("hello")) # True
print(bool(""))      # False
print(bool())        # False — no argument defaults to False
```

Rule: zero and empty → `False`, everything else → `True`

Full rules of truthiness come in Part 12 — for now, this is the mental model.

## Gotcha — `bool("False")` is `True`

```python
print(bool("False"))   # True — surprise!
print(bool("0"))       # True — also surprise!
```

`"False"` is a non-empty string → truthy.

Python does not read the text and interpret it — it checks if the string is empty or not.

Only `bool("")` is `False` — any other string, even `"False"` or `"0"`, is `True`.

This catches beginners who read data from files or user input as strings.

# Comparison Operators

Compare two values → produce a boolean result (`True` or `False`).

These are how your program asks yes/no questions about data.

```python
a = 10
b = 20

print(a == b)    # False  (equal to)
print(a != b)    # True   (not equal to)
print(a > b)     # False  (greater than)
print(a < b)     # True   (less than)
print(a >= 10)   # True   (greater than or equal to)
print(a <= 5)    # False  (less than or equal to)
```

| Operator | What It Asks              | Example    | Result  |
| -------- | ------------------------- | ---------- | ------- |
| `==`     | Are they equal?           | `10 == 10` | `True`  |
| `!=`     | Are they different?       | `10 != 5`  | `True`  |
| `>`      | Is left bigger?           | `10 > 5`   | `True`  |
| `<`      | Is left smaller?          | `10 < 5`   | `False` |
| `>=`     | Is left bigger or equal?  | `10 >= 10` | `True`  |
| `<=`     | Is left smaller or equal? | `5 <= 10`  | `True`  |

## What Happens in Memory When You Compare

Every comparison produces a boolean object.

But since `True` and `False` are singletons → no new object is created.

Result just points to the existing `True` or `False` in the heap.

```python
result = (10 > 5)

print(result)       # True
print(id(result))   # same id as every other True
```

Millions of comparisons, but only two boolean objects ever exist.

This is efficient — Python does not waste memory on repeated `True`/`False` objects.
