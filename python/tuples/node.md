---
title: Tuples
type: lesson
---

# Tuples

A **tuple** is an ordered collection of values — like a list, but **immutable** (you can't change it after creating it). Tuples are perfect for grouping a fixed bundle of related values together.

---

## Creating a Tuple

Round brackets, comma-separated:

```python
book = ("The Hobbit", "J.R.R. Tolkien", 1937)
```

The brackets are optional — what actually makes it a tuple is the commas:

```python
point = 3, 4
print(point)        # (3, 4)
print(type(point))  # <class 'tuple'>
```

A **one-item tuple** needs a trailing comma to be distinguished from a plain value in brackets:

```python
not_a_tuple = (5)
yes_a_tuple = (5,)
```

---

## Accessing Items

Same indexing as lists:

```python
book = ("The Hobbit", "J.R.R. Tolkien", 1937)
print(book[0])      # The Hobbit
print(book[-1])     # 1937
```

---

## Immutability

Once a tuple exists, you can't change its contents:

```python
book[0] = "Different Title"     # TypeError!
```

If you need to "change" a tuple, build a new one.

---

## Unpacking

The really useful trick: assign each item of a tuple to its own variable in one line.

```python
book = ("The Hobbit", "J.R.R. Tolkien", 1937)
title, author, year = book

print(f"'{title}' by {author}, published in {year}")
```

This is called **tuple unpacking** and shows up everywhere — swapping variables, iterating dicts, returning multiple values from a function.

### Swapping with unpacking

```python
a, b = 1, 2
a, b = b, a
print(a, b)         # 2 1
```

### Reordering a tuple

```python
book = ("The Hobbit", "J.R.R. Tolkien", 1937)
swapped = (book[2], book[1], book[0])   # (year, author, title)
print(swapped)
```

---

## Practice

1. Think of your favourite book. Create a tuple `book = (title, author, year)`.

2. Unpack it into three variables and print using an f-string:
   ```python
   title, author, year = book
   print(f"'{title}' by {author}, published in {year}")
   ```

3. Repeat for a different book:
   ```python
   book2 = ("Dune", "Frank Herbert", 1965)
   t, a, y = book2
   print(f"'{t}' by {a}, published in {y}")
   ```

4. Swap the order to `(year, author, title)`. Unpack the swapped version and observe the result.

---

## Question

How does tuple unpacking make your code more readable than indexing with `book[0]`, `book[1]`, `book[2]`?

---

**Next up:** **Sets** — collections of unique values where duplicates can't exist.
