# Logical Operators

Logical operators combine multiple conditions into one expression.

## and — Both must be True

```python
age = 25
has_id = True

print(age >= 18 and has_id)   # True
print(age >= 18 and not has_id)  # Would be False if has_id was False
```

and returns True only if both sides are True.

## or — At least one must be True

```python
is_student = False
is_employee = True

print(is_student or is_employee)   # True
```

or returns True if at least one side is True.

## not — Reverses the boolean

```python
is_active = True
print(not is_active)   # False
```

## The Critical Detail: and/or Return VALUES, Not True/False

Most tutorials teach that and returns True or False. That is incomplete. In Python, and and or return one of the actual operands, not a boolean:

```python
print("hello" and "world")   # "world"  — NOT True
print("" and "world")        # ""       — NOT False

print("hello" or "world")    # "hello"  — NOT True
print("" or "world")         # "world"  — NOT True

print(0 or 42)               # 42       — NOT True
print(None or "default")     # "default"
```

The rule:

* and returns the first falsy value it finds, or the last value if all are truthy
* or returns the first truthy value it finds, or the last value if all are falsy

This is not academic — senior developers use this for default values:

```python
username = input("Name: ") or "Anonymous"
```
