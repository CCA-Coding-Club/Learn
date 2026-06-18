---
title: Dictionary Comprehensions
type: lesson
---

# Dictionary Comprehensions

A **dictionary comprehension** builds a dict in one line. Same pattern as list and set comprehensions, but with a `key: value` expression.

---

## The Shape

```text
{ key: value  for item in iterable  if condition }
```

The colon between `key` and `value` is what makes it a dict.

---

## Example: Character → ASCII Code

`ord(ch)` gives the numeric code for a character. Pair every character of a word with its code:

```python
d = {ch: ord(ch) for ch in "PYTHONIC"}
print(d)
# {'P': 80, 'Y': 89, 'T': 84, 'H': 72, 'O': 79, 'N': 78, 'I': 73, 'C': 67}
```

The lowercase version:

```python
d_lower = {ch: ord(ch) for ch in "pythonic"}
print(d_lower)
# {'p': 112, 'y': 121, 't': 116, ...}
```

---

## Example: Numbers → Squares

```python
squares = {n: n ** 2 for n in range(5)}
print(squares)
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

Now `squares[3]` gives you `9` — a fast lookup table.

---

## Example: Flipping a Dict

Swap keys and values:

```python
ages = {"Alice": 30, "Bob": 25}
by_age = {age: name for name, age in ages.items()}
print(by_age)
# {30: 'Alice', 25: 'Bob'}
```

---

## What is `ord()`?

`ord(ch)` returns the numeric code (the **Unicode code point**) for a single character. `chr(n)` does the reverse. They're handy for cipher-style problems.

```python
print(ord('A'))     # 65
print(chr(65))      # A
```

---

## Practice

1. Map every character of `"PYTHONIC"` to its `ord()` value with a dict comprehension. Print the dict.

2. Repeat with `"pythonic"` (lowercase). Compare the two — what changed?

3. Build a dict that maps `0..4` to their squares.

4. **Experiment:** map every word in a small list to its length.

---

## Question

What does `ord()` return, and why is a dict comprehension the natural way to build a character-to-code lookup table?

---

**Next up:** Test everything from Worksheet 3 in the **Challenge**.
