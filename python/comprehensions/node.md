---
title: Comprehensions Refresher
type: lesson
---

# Comprehensions Refresher

You've seen list, set, and dict comprehensions individually. This lesson is a quick refresher so you can pick the right shape without thinking — and warms you up for the rest of Worksheet 4.

---

## The Three Shapes Side by Side

| Shape | Brackets | Builds | When to use                                 |
|-------|----------|--------|---------------------------------------------|
| List  | `[ ]`    | `list` | Order matters; duplicates allowed           |
| Set   | `{ }`    | `set`  | Only unique items                           |
| Dict  | `{k:v}`  | `dict` | Pairs of key → value                        |

```python
[n**2 for n in range(5)]               # [0, 1, 4, 9, 16]
{n**2 for n in range(5)}               # {0, 1, 4, 9, 16}
{n: n**2 for n in range(5)}            # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

---

## Practice

### 1. List Comprehension — Squares

Use a list comprehension to create a list of squares for the numbers 1 through 5.

```python
numbers = [1, 2, 3, 4, 5]
squares = [n ** 2 for n in numbers]
print(squares)
# [1, 4, 9, 16, 25]
```

---

### 2. Set Comprehension — First Letters

Build a set of all unique first letters from `["apple", "banana", "avocado", "cherry"]`.

```python
fruits = ["apple", "banana", "avocado", "cherry"]
first_letters = {word[0] for word in fruits}
print(first_letters)
# {'a', 'b', 'c'}
```

`'a'` only appears once even though two words start with it — that's the magic of a set.

---

### 3. List Comprehension with `if` — Even Numbers

Build a list of all even numbers from 0 to 10.

```python
evens = [n for n in range(11) if n % 2 == 0]
print(evens)
# [0, 2, 4, 6, 8, 10]
```

---

## Try It Yourself

- Build a list of `n * 10` for every `n` in `range(1, 6)`.
- Build a set of vowels from any sentence (use a set comprehension).
- Build a dict mapping each word in a list to its length.

---

## Question

How do you decide between a list, set, or dict comprehension for a given problem?

---

**Next up:** **Functions in Depth** — defaults, return values, and combining functions with what you've learned.
