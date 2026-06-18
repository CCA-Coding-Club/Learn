---
title: Tuples in Lists
type: lesson
---

# Tuples in Lists

A list of tuples is one of the most common shapes of data you'll meet in Python — records, score tables, key-value pairs, x/y coordinates. Combined with `max()`, `min()`, and `sorted()`, you can answer real questions in just a few lines.

---

## The Shape

Each tuple is one "record"; the list is the whole table.

```python
scores = [
    ("Alice", 92),
    ("Bob", 85),
    ("Chris", 97),
]
```

That's three records, each with a name and a score.

---

## Looping Over Records

Unpack as you go:

```python
for name, score in scores:
    print(f"{name}: {score}")
```

---

## Finding the Highest Score with `max()`

By default, `max(scores)` would compare the tuples themselves — which works, but compares the **names** first (alphabetically). What you want is to compare by the **second item** of each tuple.

Use the `key=` argument:

```python
best = max(scores, key=lambda x: x[1])
print(best[0], best[1])     # Chris 97
```

`lambda x: x[1]` is a tiny anonymous function that says "for each tuple `x`, look at `x[1]`" — the score.

### Finding the lowest score

```python
worst = min(scores, key=lambda x: x[1])
print(worst[0], worst[1])   # Bob 85
```

---

## Sorting by Score

`sorted` uses the same `key=` trick:

```python
ranked = sorted(scores, key=lambda x: x[1], reverse=True)
print(ranked)
# [('Chris', 97), ('Alice', 92), ('Bob', 85)]
```

---

## Practice

1. Create a list of `(name, score)` tuples for at least three people.

2. Print every record with a nicely formatted f-string.

3. Find the **highest** score with `max(... key=...)`. Print the name and score.

4. Find the **lowest** score with `min(... key=...)`. Print the name and score.

5. **Reflect:** swap in different data (e.g. `(item, price)` for a shop). Does the same code work? Why?

---

## Question

How does the `key=` argument to `max()` simplify the problem compared to writing your own loop?

---

**Next up:** **Merging Dictionaries** — combining two dicts into one.
