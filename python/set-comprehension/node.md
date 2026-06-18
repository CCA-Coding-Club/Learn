---
title: Set Comprehensions
type: lesson
---

# Set Comprehensions

A **set comprehension** is the same idea as a list comprehension — but with curly braces, producing a set instead of a list. Use one whenever you want to gather *unique* items from a loop.

---

## The Shape

```text
{ expression  for item in iterable  if condition }
```

The only difference from a list comprehension: curly braces instead of square ones. Duplicates are silently dropped.

---

## Example: Unique Letters

```python
s = "Elegant examples excite everyone."

letters = {ch for ch in s.lower() if ch.isalpha()}
print(letters)
# {'e', 'l', 'g', 'a', 'n', 't', 'x', 'm', 'p', 's', 'c', 'i', 'y', 'o', 'r'}
```

You get every unique letter that appears in the sentence, ignoring case and punctuation.

---

## Example: First Letters of Words

```python
fruits = ["apple", "banana", "avocado", "cherry"]
first_letters = {word[0] for word in fruits}
print(first_letters)
# {'a', 'b', 'c'}
```

Even though "apple" and "avocado" both start with `'a'`, the set only has it once.

---

## Filtering: Just the Consonants

```python
s = "Elegant examples excite everyone."
letters = {ch for ch in s.lower() if ch.isalpha()}

consonants = {ch for ch in letters if ch not in 'aeiou'}
print(consonants)
```

---

## List vs Set Comprehensions

| Use a list comprehension when... | Use a set comprehension when... |
|----------------------------------|---------------------------------|
| Order matters                    | Order doesn't matter            |
| Duplicates matter                | You want unique items           |
| You'll index into it later       | You'll just check membership    |

---

## Practice

1. Type a string into a variable `s`.

2. Build a set of every unique **lowercase letter** that appears in it.

3. Print your set.

4. Filter the set down to just the **consonants** (letters not in `'aeiou'`).

5. **Reflect:** print both sets and notice the difference.

---

## Question

Why is a set comprehension a more efficient way to gather unique items than a list comprehension + manual dedup?

---

**Next up:** **Dictionary Comprehensions** — building dicts in one line.
