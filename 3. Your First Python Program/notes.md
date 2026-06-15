## The Python Interactive Shell (REPL)

### Open your terminal and type:

```bash
python
```

> **Note:** On Mac/Linux, use `python3`.

---

### You will see:

```python
>>>
```

This is the **REPL** — **Read, Evaluate, Print, Loop**.

| Step | Description |
|--------|-------------|
| **Read** | Python reads what you type |
| **Evaluate** | Python executes it |
| **Print** | Python shows the result |
| **Loop** | Python waits for the next input |

---

### Purpose

The REPL is useful for quick experiments and testing small pieces of code.

It is **not meant for building applications**.

---

### Try this:

```python
>>> 2 + 3
5

>>> "hello"
'hello'
```

---

### To exit the REPL:

```python
>>> exit()
```
## The Full Power of `print()`

Most developers use only the basic form of `print()`, but it provides several useful parameters:

```python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

---

### `sep` — Change What Goes Between Values

By default, `print()` separates values with a space.

```python
print("Python", "Java", "C++")
# Output: Python Java C++

print("Python", "Java", "C++", sep=", ")
# Output: Python, Java, C++

print(2026, 3, 17, sep="-")
# Output: 2026-3-17
```

---

### `end` — Change What Comes After Output

By default, `print()` moves to a new line (`\n`).

```python
print("Loading", end="...")
print("Done!")
# Output: Loading...Done!

print("One", end=" → ")
print("Two", end=" → ")
print("Three")
# Output: One → Two → Three
```

---

### `file` — Write Output to a File

Instead of displaying output on the screen, `print()` can write directly to a file.

```python
with open("log.txt", "w") as f:
    print("App started", file=f)
    print("User logged in", file=f)
```

Output is stored in `log.txt` instead of the terminal.

---

### `flush` — Force Immediate Output

Python may temporarily hold output before displaying it. `flush=True` forces immediate output.

```python
import time

print("Step 1...", flush=True)
time.sleep(1)

print("Step 2...", flush=True)
time.sleep(1)

print("Done!", flush=True)
```

Useful for progress updates and real-time logging.

---

### Quick Reference

| Parameter | Purpose |
|------------|---------|
| `sep` | Changes separator between values |
| `end` | Changes ending character/string |
| `file` | Sends output to a file |
| `flush` | Forces immediate output |

### Quick Reference: Common `print()` Patterns

| What You Want | Code | Output |
|--------------|------|--------|
| Basic output | `print("hello")` | `hello` |
| Multiple values | `print("a", "b", "c")` | `a b c` |
| Custom separator | `print("a", "b", sep="-")` | `a-b` |
| No newline | `print("hi", end="")` | `hi` |
| Custom ending | `print("hi", end="!")` | `hi!` |
| Print to file | `print("log", file=f)` | Writes to file |
| Force instant output | `print("ok", flush=True)` | Immediate output |
| Empty line | `print()` | Blank line |
| Visual separator | `print("=" * 30)` | `==============================` |
| Repeat string | `print("Ha" * 3)` | `HaHaHa` |
| Reveal hidden characters | `print(repr(text))` | Shows `\n`, `\t`, etc. |

## `input()` — Receiving Data from the User

`input()` pauses the program and waits for the user to type something.

```python
name = input("Enter your name: ")
print("Hello,", name)
```

When this runs:

```text
Enter your name: OnePercentDev
Hello, OnePercentDev
```

The text inside `input()` is called a **prompt** — it tells the user what to type.

---

### Important: `input()` Always Returns a String

Everything that comes from `input()` is a **string (text)**, even if the user types a number.

```python
age = input("Enter your age: ")
print(type(age))
```

Output:

```text
<class 'str'>
```

Even if you type `25`, Python treats it as the text `"25"`, not the number `25`.

---

### Converting Input to a Number

To work with numbers from input, convert using `int()` or `float()`:

```python
age = int(input("Enter your age: "))
print(type(age))
```

Output:

```text
<class 'int'>
```

Now `age` is an actual number and you can do math with it.

---

### Quick Reference

| Function | Purpose |
|----------|---------|
| `input()` | Receive user input |
| `int()` | Convert text to integer |
| `float()` | Convert text to decimal number |

### Examples

```python
age = int(input("Enter your age: "))
```

```python
price = float(input("Enter the price: "))
```
