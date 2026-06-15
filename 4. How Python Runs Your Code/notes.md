# The Python Execution Pipeline

## Overview

When a Python program runs, it goes through the following stages:

```text
Source Code
    ↓
Lexing (Tokenization)
    ↓
Parsing (AST)
    ↓
Compilation (Bytecode)
    ↓
Python Virtual Machine (PVM)
    ↓
Output
```

---

## 1. Source Code

### Definition

The Python code written in a `.py` file.

### Example

```python
x = 10
print(x)
```

## 2 — Lexing (Tokenization)

Before Python can understand your code, it first breaks the raw text into small meaningful pieces called **tokens**.

This step is called **lexing** (or **tokenization**).

### Example

When Python reads:

```python
x = 10
```

it sees it as one long string of characters:

```text
x,  , =,  , 1, 0
```

Lexing splits it into individual tokens:

| Token | Type |
|---------|---------|
| `x` | NAME (variable name) |
| `=` | OP (operator) |
| `10` | NUMBER (integer) |

Each token is the smallest meaningful unit — a name, a symbol, or a number.

## 3. Parsing

Once Python has the tokens, it structures them into an **Abstract Syntax Tree (AST)** — a tree that represents the meaning of your code.

Lexing gave Python the individual words.

Parsing figures out the grammar — how those words relate to each other.

For:

```python
x = 10
```

parsing understands:

> "this is an assignment, the left side is a variable name called x, the right side is the number 10."

## 4. Compilation to Bytecode

### Definition

Python converts the parsed code into **bytecode**.

### Bytecode Characteristics

* Lower-level representation of Python code
* Not machine code
* Platform-independent
* Stored as `.pyc` files

### Example

```text
Source Code
    ↓
Bytecode
```

### Why Bytecode?

* Faster execution on repeated runs
* Works across different operating systems
* Supports portability

### Related Folder

```text
__pycache__/
```

Contains cached bytecode files.

---

## 5. Python Virtual Machine (PVM)

### Definition

The Python Virtual Machine executes bytecode instructions.

### Responsibilities

* Execute bytecode
* Manage memory
* Handle function calls
* Control program execution

### Process

```text
Bytecode
    ↓
PVM
    ↓
Execution
```

### Important Note

The PVM is part of the Python interpreter and is responsible for running Python programs.

---

## 6. Output

### Definition

The final result produced by the program.

### Example

```python
print("Hello")
```

Output:

```text
Hello
```

### Output Destinations

* Terminal
* Files
* Databases
* APIs
* Web Applications

---

## Quick Reference

| Stage       | Purpose                          |
| ----------- | -------------------------------- |
| Source Code | Python code written by developer |
| Lexing      | Converts text into tokens        |
| Parsing     | Checks syntax and builds AST     |
| Compilation | Converts AST into bytecode       |
| PVM         | Executes bytecode                |
| Output      | Produces result                  |

---

## The Complete Picture

When you run:

```bash
python main.py
```

The following steps occur:

1. The operating system loads the Python interpreter (**CPython**) into RAM.
2. CPython reads your `.py` file from disk.
3. It breaks the source code into tokens (**lexing**).
4. It structures the tokens into an Abstract Syntax Tree (**parsing**).
5. It compiles the AST into bytecode.
6. The Python Virtual Machine (**PVM**) executes the bytecode.
7. Output is sent to the screen.

All of this happens in milliseconds for simple programs.
