## Where Does Data Live When a Program Runs?

### Not on the Hard Disk

The hard disk is used for **permanent storage**:

* Files
* Photos
* Videos
* Programs

When a program is running, it does not operate directly from the hard disk because disk access is relatively slow.

---

### Not in the CPU

The CPU executes instructions and performs calculations.

It processes data but does not store program data long-term.

---

### Data Lives in RAM

RAM (Random Access Memory) is the computer's **working memory**.

When a program runs, its active data is stored in RAM.

---

### Simple Analogy

| Component | Analogy   | Purpose                     |
| --------- | --------- | --------------------------- |
| Hard Disk | Bookshelf | Permanent storage           |
| RAM       | Desk      | Active workspace            |
| CPU       | Brain     | Processing and calculations |

When you need a book, you move it from the bookshelf to your desk.

Similarly, programs are loaded from the hard disk into RAM before execution.

---

## When Does This Happen?

### Saving a File

When you save:

```text
main.py
```

the file is stored on the hard disk.

Nothing is running yet.

```text
Save file → Stored on disk
```

---

### Running a Program

When you run:

```bash
python3 main.py
```

the operating system:

1. Loads the Python interpreter into RAM.
2. Loads your program into RAM.
3. Starts execution.

```text
Run Program → Loaded into RAM → Execution Begins
```

---

## Programs Use RAM

Every running application occupies RAM.

Examples:

* VS Code
* Chrome
* Spotify
* Terminal
* Python Programs

Each running application receives its own portion of memory from the operating system.

---

### Why Computers Slow Down

Opening many applications increases RAM usage.

```text
More Programs Running
            ↓
More RAM Used
            ↓
Less Free Memory Available
            ↓
Slower System Performance
```

---

## What Is RAM Really?

RAM is a large collection of memory locations.

All memory locations are identical.

RAM does not contain built-in sections such as:

* Stack
* Heap

These sections are created by software.

---

## Stack and Heap

### Important Point

Stack and Heap are **software concepts**, not hardware components.

RAM is simply a large block of memory.

Programs organize this memory into different regions based on how the data will be used.

---

### Analogy

Think of RAM as a blank notebook.

```text
Blank Notebook = RAM
```

The notebook contains empty pages.

You decide:

```text
Pages 1–50   → Quick Notes
Pages 51–200 → Detailed Work
```

The notebook does not know the difference.

You create the organization.

Similarly:

```text
RAM = Memory
Stack = Organized Region
Heap = Organized Region
```

The operating system and runtime create these regions to manage memory efficiently.

## Stack vs Heap Memory

| Feature | Stack | Heap |
|----------|--------|------|
| Purpose | Stores function calls and local variables | Stores actual objects and data |
| Speed | Faster | Slower |
| Memory Management | Automatic | Managed by Python |
| Lifetime | Removed when function ends | Exists until no longer needed |
| Examples | Function parameters, local variables | Strings, Lists, Dictionaries, Objects |

### Example

```python
name = "Vishwas"
numbers = [10, 20, 30]
```

| Variable | Stored In |
|-----------|-----------|
| `name` | Stack (reference) |
| `"Vishwas"` | Heap |
| `numbers` | Stack (reference) |
| `[10, 20, 30]` | Heap |

### Memory Flow

```text
Variable Name → Stack
Actual Data   → Heap
```

## What Happens When You Run `python3 main.py`

### Execution Flow

```text
python3 main.py
       ↓
OS loads CPython into RAM
       ↓
CPython reads main.py
       ↓
Lexing → Parsing → Bytecode
       ↓
PVM executes bytecode
       ↓
Variable created
       ↓
Program Output
       ↓
Program Ends
```

---

### Example

Code:

```python
x = 10
```

### Memory Flow

```text
PVM executes x = 10
        ↓
Creates value 10 in Heap
        ↓
Creates name x
        ↓
x points to 10
```

```text
Stack                  Heap
-----                  -----
x         ─────────▶   10
```

---

## What Happens When the Program Ends?

When the program finishes:

* Stack memory is cleared
* Heap memory is released
* Variables are destroyed
* Memory is returned to the operating system

### Example

```text
Run 1
python3 main.py
x = 10
Program Ends
Memory Freed
```

```text
Run 2
python3 main.py
Starts Fresh
x does not exist
```

### Key Point

Each program execution starts with a fresh memory space.

Variables from previous runs do not exist after the program ends.

## Variable Assignment and Memory References

### Step 1: `x = 10`

```python
x = 10

print(f"x = {x}")
print(f"id(x) = {id(x)}")
```

Output:

```text
x = 10
id(x) = 4392513792
```

### Memory View

```text
STACK                     HEAP
┌──────┐               ┌────────────┐
│  x  ───────────────▶ │ value: 10  │
└──────┘               └────────────┘
```

---

### Step 2: `y = x`

```python
y = x

print(f"x = {x}")
print(f"y = {y}")

print(f"id(x) = {id(x)}")
print(f"id(y) = {id(y)}")

print(f"Same id? {id(x) == id(y)}")
```

Output:

```text
x = 10
y = 10

id(x) = 4392513792
id(y) = 4392513792

Same id? True
```

### Memory View

```text
STACK                     HEAP
┌──────┐               ┌────────────┐
│ x ────────────────▶ │ value: 10  │
│ y ────────────────▶ │            │
└──────┘               └────────────┘
```

### Observation

* No new value is created.
* `x` and `y` reference the same object.
* Same `id()` means same object in memory.

---

### Step 3: `x = 20`

```python
x = 20

print(f"x = {x}")
print(f"y = {y}")

print(f"id(x) = {id(x)}")
print(f"id(y) = {id(y)}")

print(f"Same id? {id(x) == id(y)}")
```

Output:

```text
x = 20
y = 10

id(x) = 4392514112
id(y) = 4392513792

Same id? False
```

### Memory View

```text
STACK                     HEAP
┌──────┐               ┌────────────┐
│ x ────────────────▶ │ value: 20  │
│                    │            │
│ y ────────┐         └────────────┘
└──────┘    └──────▶ ┌────────────┐
                     │ value: 10  │
                     └────────────┘
```

### Observation

* A new object is created for `20`.
* `x` now references the new object.
* `y` continues to reference `10`.
* Reassignment changes the reference, not the original object.

---

## What `id()` Returns

### Definition

`id()` returns the unique identity of an object during its lifetime.

```python
x = 10

print(id(x))
```

### Usage

| Condition        | Meaning           |
| ---------------- | ----------------- |
| Same `id()`      | Same object       |
| Different `id()` | Different objects |

### Example

```python
x = 10
y = x

print(id(x) == id(y))
```

Output:

```text
True
```

---

## Garbage Collection

### Definition

When no variable references an object, it becomes eligible for garbage collection.

### Example

```python
x = 10
x = 20
```

### Memory View

```text
STACK                     HEAP
┌──────┐               ┌────────────┐
│ x ────────────────▶ │ value: 20  │
└──────┘               └────────────┘

                       ┌────────────┐
                       │ value: 10  │
                       └────────────┘
```

### What Happens?

1. `x` initially references `10`.
2. `x` is reassigned to `20`.
3. No variable references `10`.
4. Python's garbage collector can remove the unused object.

### Key Point

Objects with no references become eligible for memory cleanup.
