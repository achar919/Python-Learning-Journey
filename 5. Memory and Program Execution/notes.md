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
