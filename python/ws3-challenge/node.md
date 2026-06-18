---
title: "Challenge: Worksheet 3"
type: challenge
---

# Challenge: Worksheet 3

Put sets, tuples, dictionaries, comprehensions, and string tricks together to build something cool.

---

## Requirements

Complete **at least 2 out of the 5** challenges below. Put your finished work in a separate file (e.g. `ws3_challenge.py`) and let the President or VP know which you'll be doing before you start.

---

## Challenge 1: Keyword Search Tool

Write a program that:

1. Reads a paragraph from the user.
2. Splits it into words.
3. Asks for a **keyword**.
4. Reports the keyword's **frequency**, **highlights** every appearance, and prints any **sentences** containing it.

> Try: `.count()`, `.replace()`, `.split()`

---

## Challenge 2: Student Score Tracker

Use a dictionary that maps **student names** to **tuples of quiz scores**:

```python
scores = {
    "Alice": (88, 92, 79),
    "Bob": (70, 85, 90),
    "Chris": (95, 91, 87),
}
```

Write functions to:

- Add a new student
- Update an existing student's scores
- Calculate the **top** and **bottom** averages

> Try: dict + tuple operations, list comprehensions

---

## Challenge 3: Custom Text Formatter

Transform a sentence:

- Replace spaces with another character
- **Capitalize the vowels** while leaving consonants alone
- Count the number of **unique consonants** used

> Try: string methods + set comprehensions + f-strings

---

## Challenge 4: Data Summary Dashboard

Given a list of product dictionaries:

```python
products = [
    {"name": "Apple", "price": 1.20, "qty": 50},
    {"name": "Avocado", "price": 2.50, "qty": 20},
    {"name": "Banana", "price": 0.50, "qty": 100},
]
```

Display:

- Total inventory value (sum of `price * qty` for each)
- Most expensive item
- A **set of unique names**
- A **set of unique first initials**

> Try: for-loops, comprehensions, dict access

---

## Challenge 5: Puzzle Generator

Create a list of tuples pairing each word with its length:

```python
[("apple", 5), ("banana", 6), ("kiwi", 4)]
```

Shuffle it (use the `random` library), then prompt the user to match each word to its length.

> Try: tuples, lists, `random.shuffle`

---

## Reflection

- Which activity was most exciting or challenging? Why?
- What new skills or concepts stood out as especially useful?
- How could you use these techniques in your own projects?
