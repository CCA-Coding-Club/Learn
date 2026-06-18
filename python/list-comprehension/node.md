---
title: List Comprehensions
type: lesson
---

# List Comprehensions

A **list comprehension** is a one-line way to build a list from a loop. Once you get used to them, they make a huge class of code shorter and more readable.

---

## From Loop to Comprehension

The long way:

```python
squares = []
for n in range(1, 21):
    if n % 2 == 0:
        squares.append(n ** 2)
```

The short way:

```python
squares = [n ** 2 for n in range(1, 21) if n % 2 == 0]
```

Both produce the same list of squares of even numbers from 2 to 20.

---

## The Shape

```text
[ expression  for item in iterable  if condition ]
```

| Part                  | What it does                                   |
|-----------------------|------------------------------------------------|
| `expression`          | What to put in the new list (per item)         |
| `for item in iterable`| Loop over a list, range, string, etc.          |
| `if condition`        | (Optional) keep only items matching this       |

---

## Examples

### Squares of every number 1–10

```python
squares = [n ** 2 for n in range(1, 11)]
# [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

### Only even numbers 0–10

```python
evens = [n for n in range(11) if n % 2 == 0]
# [0, 2, 4, 6, 8, 10]
```

### Uppercase every word in a list

```python
words = ["hello", "world"]
shout = [w.upper() for w in words]
# ['HELLO', 'WORLD']
```

### Lengths of strings

```python
lengths = [len(w) for w in ["apple", "banana", "kiwi"]]
# [5, 6, 4]
```

---

## When *Not* To Use a Comprehension

If the expression gets long, or the condition gets complicated, a regular `for` loop is more readable. Comprehensions shine when each piece is short.

---

## Practice

1. Write a `for` loop that builds a list of squares for the even numbers between 1 and 20.

2. Rewrite the same thing as a list comprehension. Compare them — which feels clearer?

3. Build a list of all numbers from 1–20 that are **divisible by 4**:
   ```python
   quads = [n for n in range(1, 21) if n % 4 == 0]
   ```

4. Build a list of **cubes** of every **odd** number from 1–20.

5. **Reflect:** print all three lists and compare.

---

## Question

How does a list comprehension make your code more concise and readable than a loop with `.append()`?

---

**Next up:** **Set Comprehensions** — the same idea but producing a set.
