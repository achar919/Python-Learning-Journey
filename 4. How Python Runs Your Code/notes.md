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

---

## 2. Lexing (Tokenization)

### Definition

Python breaks source code into small meaningful units called **tokens**.

### Example

Code:

```python
x = 10
```

| Token | Category | Purpose |
|---------|---------|---------|
| `x` | Variable | Stores data |
| `=` | Assignment Operator | Assigns a value |
| `10` | Integer | Data being stored |

### Result

```text
Variable x receives the value 10.
```

## 3. Parsing

### Definition

Python checks whether the tokens follow valid Python syntax and builds an **Abstract Syntax Tree (AST)**.

### Example

```python
x = 10
```

Python understands:

* Assignment operation
* Variable name: `x`
* Value: `10`

### Purpose

* Validates syntax
* Creates program structure

### Common Error

```python
x = = 10
```

Results in a syntax error during parsing.

---

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
