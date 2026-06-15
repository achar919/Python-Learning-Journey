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

### Definition

`input()` pauses the program and waits for the user to enter data.

### Syntax

```python
variable = input("Prompt Message")
```

### Example

```python
name = input("Enter your name: ")
print("Hello,", name)
```

**Output**

```text
Enter your name: Vishwas
Hello, Vishwas
```

### Prompt

The text inside `input()` is called a **prompt**.

```python
input("Enter your name: ")
```

Here, `"Enter your name: "` is the prompt displayed to the user.

---

### Important Rule

`input()` always returns a **string (`str`)**.

```python
age = input("Enter your age: ")
print(type(age))
```

**Output**

```text
<class 'str'>
```

Even if the user enters:

```text
25
```

Python treats it as:

```python
"25"
```

not

```python
25
```

---

### Converting Input to Numbers

Use `int()` for whole numbers.

```python
age = int(input("Enter your age: "))
```

Use `float()` for decimal numbers.

```python
salary = float(input("Enter your salary: "))
```

### Example

```python
age = int(input("Enter your age: "))
print(type(age))
```

**Output**

```text
<class 'int'>
```

Now Python treats `age` as a number, allowing mathematical operations.

---

### Quick Reference

| Function  | Purpose            | Example          |
| --------- | ------------------ | ---------------- |
| `input()` | Receive user input | `name = input()` |
| `int()`   | Convert to integer | `int("25")`      |
| `float()` | Convert to decimal | `float("3.14")`  |

## f-strings — Clean Output Formatting

Python provides a clean way to embed values inside strings using **f-strings** (formatted string literals).

### Example

```python
name = "Vishwas"
age = 25

print(f"My name is {name} and I am {age} years old")
```

Output:

```text
My name is Vishwas and I am 25 years old
```

The `f` before the quotes tells Python to look for `{}` placeholders and replace them with actual values.

f-strings are the modern, preferred way to format output in Python.

---

### f-string Formatting Tricks

```python
print(f"{1400000000:,}")
# Output: 1,400,000,000

print(f"{0.9534:.1%}")
# Output: 95.3%

print(f"{0.85:.0%}")
# Output: 85%

print(f"{'Python':*^20}")
# Output: *******Python*******
```

### Quick Reference

| Format | What It Does | Example Output |
|----------|----------|----------|
| `:,` | Add commas to numbers | `1,000,000` |
| `:.1%` | Percentage with 1 decimal | `95.3%` |
| `:.0%` | Percentage, no decimal | `85%` |
| `:*^20` | Center and fill with `*` | `*******Python*******` |
| `:<20` | Left-align in 20 characters | `Python              ` |
| `:>20` | Right-align in 20 characters | `              Python` |

---

## The Fundamental Program Model

Every program follows the same core model:

```text
Input → Process → Output
```

### Process Flow

| Step | What Happens | Example |
|--------|-------------|---------|
| Input | Data comes in | Vishwas enters a number |
| Process | Program works on the data | Calculate the square of the number |
| Output | Result goes out | Display the answer |

### Real-World Examples

| Application | Input | Process | Output |
|------------|--------|---------|---------|
| Calculator | Numbers | Calculation | Result |
| Web API | Request | Business Logic | Response |
| AI Model | Prompt | Model Processing | Generated Text |
| Data Pipeline | Raw Data | Transform Data | Store Result |

Every system you build follows this pattern.
## References

The concepts and learning structure used in these notes were inspired by the following repository:

* [One Percent Dev](https://github.com/Shyamiscoding/onepercentdev?utm_source=chatgpt.com)

### Note

These notes are my personal revision notes created during my Python learning journey.

The content has been summarized, reorganized, and rewritten in my own format for quick revision, long-term memorization, and practical understanding.
