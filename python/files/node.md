---
title: Working with Files
type: lesson
---

# Working with Files

Reading from and writing to files is how programs **persist** data — keeping it around after the program exits. Python's `with` statement makes this clean and safe.

---

## The `with` Pattern

Always use `with open(...)` rather than calling `open()` and `close()` yourself. The `with` block closes the file for you, even if an error happens.

```python
with open("animals.txt", "w") as f:
    f.write("dog\n")
```

`f` is the file object inside the block. Once the block ends, the file is automatically closed.

---

## File Modes

| Mode  | What it does                                       |
|-------|----------------------------------------------------|
| `"r"` | Read (default). Errors if the file doesn't exist.  |
| `"w"` | Write. **Overwrites** the file, or creates it.     |
| `"a"` | Append. Adds to the end, creates if needed.        |
| `"r+"`| Read and write                                     |

---

## Writing a List to a File

```python
animals = ["dog", "cat", "rabbit"]

with open("animals.txt", "w") as f:
    for animal in animals:
        f.write(animal + "\n")
```

The `"\n"` adds a newline so each animal is on its own line.

---

## Reading a File Line by Line

```python
with open("animals.txt") as f:
    for line in f:
        print(line.strip().capitalize())
```

`line.strip()` removes the trailing newline (and any other surrounding whitespace). `capitalize()` makes the first letter uppercase.

---

## Reading the Whole File at Once

```python
with open("animals.txt") as f:
    contents = f.read()
print(contents)
```

Or as a list of lines:

```python
with open("animals.txt") as f:
    lines = f.readlines()       # ['dog\n', 'cat\n', 'rabbit\n']
```

---

## Appending

`"a"` mode adds to the end without erasing:

```python
with open("animals.txt", "a") as f:
    f.write("hamster\n")
```

If you then re-read the file, `"hamster"` is at the bottom.

---

## Handling a Missing File

```python
try:
    with open("nofile.txt") as f:
        print(f.read())
except FileNotFoundError:
    print("That file doesn't exist.")
```

---

## Practice

### 1. Save a list

```python
animals = ["dog", "cat", "rabbit"]
with open("animals.txt", "w") as f:
    for animal in animals:
        f.write(animal + "\n")
```

### 2. Read and capitalize

```python
with open("animals.txt") as f:
    for line in f:
        print(line.strip().capitalize())
```

### 3. Append a new animal

```python
with open("animals.txt", "a") as f:
    f.write("hamster\n")

with open("animals.txt") as f:
    for line in f:
        print(line.strip())
```

---

## Question

Why is `with open(...)` better than calling `open()` and `close()` yourself?

---

**Next up:** **Classes** — bundling data and behaviour into your own types.
