---
title: Dictionaries
type: lesson
---

# Dictionaries

A **dictionary** (`dict`) maps **keys** to **values**. If you need to look something up by name — counting word frequencies, tracking scores by student, configuring settings — a dict is what you want.

---

## Creating a Dictionary

Curly braces, with `key: value` pairs:

```python
ages = {
    "Alice": 30,
    "Bob": 25,
    "Carol": 28,
}
```

Empty dict:

```python
empty = {}
```

---

## Looking Up Values

```python
print(ages["Alice"])    # 30
```

Looking up a missing key raises `KeyError`:

```python
print(ages["Dave"])     # KeyError: 'Dave'
```

Use `.get()` for a safe lookup that returns `None` (or a default you choose):

```python
print(ages.get("Dave"))         # None
print(ages.get("Dave", 0))      # 0  (default)
```

---

## Adding, Updating, Removing

```python
ages["Dave"] = 40         # add (or overwrite)
ages["Alice"] = 31        # update
del ages["Bob"]           # remove
```

---

## Looping Over a Dict

| What you want    | How to loop                          |
|------------------|--------------------------------------|
| Keys             | `for k in ages:`                     |
| Values           | `for v in ages.values():`            |
| Both             | `for k, v in ages.items():`          |

```python
for name, age in ages.items():
    print(f"{name} is {age}")
```

---

## Word Frequency: The Classic Use Case

Count how often each word shows up in a paragraph:

```python
text = "Python programming is fun. Python is powerful."
words = text.split()
freq = {}

for word in words:
    freq[word] = freq.get(word, 0) + 1

print(freq)
# {'Python': 2, 'programming': 1, 'is': 2, 'fun.': 1, 'powerful.': 1}
```

`freq.get(word, 0)` returns the current count if the word is already in the dict, or `0` if it's the first time — that's the trick that makes counting clean.

### Finding the most common word

```python
most_common = max(freq, key=freq.get)
print(most_common, freq[most_common])
```

`max(freq, key=freq.get)` looks through every key and asks "which one has the highest value?"

---

## Practice

1. Write or paste a short paragraph into `text`.

2. Split it into words with `text.split()`.

3. Count each word's frequency into a dict called `freq`.

4. Print `freq`.

5. Find and print the most common word and its count.

6. Remove a word using `del freq[word]` and print the dict again.

---

## Question

Why is a dictionary perfect for tracking word counts? (Hint: what would you do with just a list?)

---

**Next up:** **Tuples in Lists** — combining the two for tasks like "find the highest score."
