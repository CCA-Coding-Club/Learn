---
title: Sets
type: lesson
---

# Sets

A **set** is an unordered collection of **unique** values. If you try to add a duplicate, the set quietly ignores it. That makes sets the natural choice any time you want to ask "what are the distinct items in this thing?"

---

## Creating a Set

Curly braces:

```python
vowels = {'a', 'e', 'i', 'o', 'u'}
```

For an empty set you have to use `set()` — `{}` creates an empty **dict**, not a set.

```python
empty = set()
```

---

## Uniqueness in Action

```python
nums = {1, 2, 2, 3, 3, 3}
print(nums)         # {1, 2, 3}
```

Adding a duplicate does nothing:

```python
nums.add(2)
print(nums)         # {1, 2, 3}
```

---

## Common Operations

| Method / op       | What it does                                |
|-------------------|---------------------------------------------|
| `s.add(x)`        | Add an item                                 |
| `s.remove(x)`     | Remove `x` (errors if missing)              |
| `s.discard(x)`    | Remove `x` (silent if missing)              |
| `x in s`          | Check membership                            |
| `len(s)`          | Number of items                             |
| `s1 \| s2`        | Union (everything in either)                |
| `s1 & s2`         | Intersection (everything in both)           |
| `s1 - s2`         | Difference (in s1 but not s2)               |

---

## Example: Unique Vowels in a Sentence

```python
sentence = "Learning Python is exciting!"

vowels_found = set()
for ch in sentence.lower():
    if ch in "aeiou":
        vowels_found.add(ch)

print(vowels_found)         # {'a', 'e', 'i', 'o', 'u'} (in some order)

vowels_found.add('y')
print(vowels_found)         # includes 'y' now

vowels_found.remove('e')
print(vowels_found)         # 'e' gone
```

The same thing using a **set comprehension** (we'll explore those soon):

```python
vowels_found = {ch.lower() for ch in sentence if ch.lower() in "aeiou"}
```

---

## Practice

1. Type any sentence into a variable.

2. Build a set of every unique vowel that appears in it.

3. Add the letter `'y'` to your set. Print it.

4. Remove `'e'`. Print it again.

5. **Reflect:** print the set after each operation so you can watch the changes.

> Reference: <https://www.pythonforbiginners.com/2025/05/python-sets-made-easy-beginner-to-pro.html>

---

## Question

What property of sets guarantees each vowel only appears once?

---

**Next up:** **Dictionaries** — pairing keys with values, perfect for lookups and counting.
