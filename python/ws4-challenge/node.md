---
title: "Challenge: Worksheet 4"
type: challenge
---

# Challenge: Worksheet 4

Combine comprehensions, functions, lambdas, files, terminal I/O, and classes into real programs.

---

## Requirements

Complete **at least 2 out of 3** of the challenges. Put your finished work in a separate file (e.g. `ws4_challenge.py`) and let the President or VP know which problems you'll be doing before you start.

---

## Challenge 1: Book Library

Write a program that:

1. Asks the user for a list of book titles, separated by commas.
2. Saves the titles to a file (one per line).
3. Reads the file back and creates a `Book` object for each title.
4. Calls each book's `display()` method to print the title.

```python
class Book:
    def __init__(self, title):
        self.title = title
    def display(self):
        print(f"Title: {self.title}")

raw = input("Enter book titles, separated by commas: ")
titles = [t.strip() for t in raw.split(",")]

with open("books.txt", "w") as f:
    for t in titles:
        f.write(t + "\n")

with open("books.txt") as f:
    for line in f:
        Book(line.strip()).display()
```

---

## Challenge 2: Unique Letters in a File

Write a function that takes a **filename** and returns a **set** of every unique letter in that file. Use a set comprehension and file reading techniques.

```python
def unique_letters(filename):
    with open(filename) as f:
        text = f.read()
    return {ch.lower() for ch in text if ch.isalpha()}

print(unique_letters("animals.txt"))
```

---

## Challenge 3: Odd Number Filter

Write a program that:

1. Asks the user to input several numbers separated by spaces.
2. Builds a list of those numbers.
3. Uses a **lambda + filter** to keep only the odd numbers.
4. Prints the odd numbers.

```python
raw = input("Enter numbers separated by spaces: ")
nums = [int(x) for x in raw.split()]
odds = list(filter(lambda n: n % 2 != 0, nums))
print(odds)
```

---

## Reflection

- Which activity was most exciting or challenging? Why?
- What new skills or concepts stood out as especially useful?
- How could you use these Python techniques in your own creative projects?
