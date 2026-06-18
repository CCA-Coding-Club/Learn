---
title: "Challenge: Worksheet 2"
type: challenge
---

# Challenge: Worksheet 2

Time to put lists, loops, errors, stacks, and functions together.

---

## Requirements

Complete **at least 7 out of 10** problems. Put your solutions in a separate file (e.g. `ws2_challenge.py`) and let the President or VP know which ones you'll be doing before you start.

---

## Problem 1: Sum a List

Create a list of numbers and use a loop to print their sum.

```python
nums = [3, 7, 2]
total = 0
# loop and add
print(total)
```

---

## Problem 2: Even Numbers 1–20

Write a loop that prints every even number from 1 to 20.

---

## Problem 3: Quit Loop

Write a loop that keeps asking the user for input until they type `'quit'`.

```python
while True:
    txt = input("> ")
    if txt == "quit":
        break
```

---

## Problem 4: Double or None

Write a function that takes a number and returns `None` if it's negative, otherwise returns double the number. Print the results for several test cases, including a negative number.

```python
def double_or_none(n):
    if n < 0:
        return None
    return n * 2
```

---

## Problem 5: Missing File

Write code that tries to open a file that doesn't exist, then catches the error and prints a friendly message.

```python
try:
    open("nofile.txt")
except FileNotFoundError:
    print("File not found!")
```

---

## Problem 6: Safe Division

Write code that divides two numbers and uses `try`/`except` to handle division by zero.

---

## Problem 7: Mini Stack

Create a stack (a list), push three numbers, pop one, and print the stack.

---

## Problem 8: Reverse a Word

Use a stack to reverse a word the user types.

```python
word = input("Enter word: ")
stack = list(word)
rev = ""
while stack:
    rev += stack.pop()
print(rev)
```

---

## Problem 9: Greet Multiple

Define `greet_user(name)` that prints `"Hello, [name]!"`. Call it with three names.

---

## Problem 10: Mini Calculator

Make a simple calculator using **four functions**: `add`, `sub`, `mul`, `div`. Each takes two numbers and returns the result. Test each one, including `div(3, 0)` — does it crash? Wrap it with `try`/`except` to handle the case.

---

## Reflection

- Which activity did you find the most challenging?
- What new concepts did you discover about lists, loops, errors, stacks, or functions?
- How do these concepts let you write bigger programs than before?
