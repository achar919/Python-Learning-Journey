# Your First Python Program

> **Note:** These notes are created for quick revision and long-term memorization during my Python learning journey.

---

## 1. Python Interactive Shell (REPL)

### Definition

REPL stands for:

- Read
- Evaluate
- Print
- Loop

It allows Python code to be executed one line at a time.

### Start REPL

```bash
python
```

### Example

```python
>>> 2 + 3
5

>>> "Hello"
'Hello'
```

### Exit REPL

```python
exit()
```

### Use Cases

- Testing code snippets
- Quick calculations
- Learning Python concepts

### Takeaway

REPL is best for experimentation and learning.

---

## 2. print()

### Definition

`print()` displays output on the screen.

### Syntax

```python
print(object)
```

### Example

```python
print("Hello, World")
```

Output:

```text
Hello, World
```

### Multiple Values

```python
print("Score:", 95)
```

Output:

```text
Score: 95
```

### Useful Parameters

| Parameter | Purpose | Example |
|-----------|---------|---------|
| `sep` | Separator between values | `print("A", "B", sep="-")` |
| `end` | Controls line ending | `print("Hi", end="!")` |
| `file` | Write output to file | `print("Log", file=f)` |
| `flush` | Force immediate output | `print("Done", flush=True)` |

### Why It Matters

`print()` is commonly used for displaying output and debugging programs.

### Takeaway

`print()` is the simplest way to communicate information from a program.

---

## 3. input()

### Definition

`input()` receives data from the user.

### Syntax

```python
input("Prompt Message")
```

### Example

```python
name = input("Enter your name: ")
print(name)
```

### Important Rule

`input()` always returns a string.

```python
age = input("Enter age: ")
print(type(age))
```

Output:

```text
<class 'str'>
```

### Convert Input to Numbers

```python
age = int(input("Enter age: "))
salary = float(input("Enter salary: "))
```

### Why It Matters

Most applications receive data from external sources such as users, files, APIs, databases, or sensors.

### Takeaway

Always remember that `input()` returns text unless converted.

---

## 4. f-strings

### Definition

f-strings allow variables and expressions to be embedded directly inside strings.

### Syntax

```python
f"Text {variable}"
```

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

### Common Formatting

| Format | Purpose | Example Output |
|----------|---------|---------|
| `:,` | Comma separator | 1,000,000 |
| `:.1f` | One decimal place | 3.1 |
| `:.2f` | Two decimal places | 3.14 |
| `:.1%` | Percentage | 95.3% |
| `:<10` | Left align | Python |
| `:>10` | Right align | Python |

### Why It Matters

f-strings are the preferred formatting method in modern Python.

### Takeaway

Use f-strings for clean and readable output.

---

## 5. Input → Process → Output

### Definition

Every program follows the same fundamental model:

```text
Input → Process → Output
```

### Example

| Step | Description |
|--------|-------------|
| Input | User enters a number |
| Process | Program performs a calculation |
| Output | Result is displayed |

### Real-World Examples

| Application | Input | Process | Output |
|------------|--------|---------|---------|
| Calculator | Numbers | Calculation | Result |
| ATM | Card & PIN | Verification | Transaction |
| Web API | Request | Business Logic | Response |
| AI Model | Prompt | Model Processing | Generated Output |

### Why It Matters

Understanding this model helps in designing any software system.

### Takeaway

Every application is built around Input, Process, and Output.

---

## 6. REPL vs Script

### Definition

Python code can be executed using either the REPL or a script file.

### Comparison

| Feature | REPL | Script |
|----------|------|---------|
| Execution | Line by line | Entire file |
| Best For | Testing | Applications |
| Saves Work | No | Yes |
| Reusable | No | Yes |

### Example Script

```python
print("Hello, Python")
```

Save as:

```text
main.py
```

Run:

```bash
python main.py
```

### Takeaway

Use REPL for testing and scripts for real projects.

---

## 7. Comments

### Definition

Comments are notes written for humans and ignored by Python.

### Syntax

```python
# Single-line comment
```

### Example

```python
# Calculate age
birth_year = 2000
age = 2026 - birth_year
```

### Best Practice

Comments should explain **why**, not **what**.

### Good Example

```python
# Using 2026 because project requirements specify it
age = 2026 - birth_year
```

### Bad Example

```python
# Subtract birth year from 2026
age = 2026 - birth_year
```

### Why It Matters

Good comments improve readability and maintainability.

### Takeaway

Write comments only when they add useful context.

---

## Quick Recap

- REPL executes Python code interactively.
- `print()` displays output and helps with debugging.
- `input()` receives user input and returns a string.
- Use `int()` and `float()` to convert numeric input.
- f-strings provide clean string formatting.
- Every application follows the Input → Process → Output model.
- Scripts are used for real projects; REPL is used for testing.
- Comments should explain why code exists.
