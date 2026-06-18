---
title: NoneType
type: lesson
---

# NoneType

`None` is Python's way of saying "no value here." It has its own type — `NoneType` — and it shows up any time a function decides it has nothing meaningful to return.

---

## What `None` Is

```python
x = None
print(x)            # None
print(type(x))      # <class 'NoneType'>
```

`None` is **not** the same as:
- `0`  — that's the number zero
- `""` — that's an empty string
- `False` — that's the boolean False

All four are "empty-ish," but they're distinct values.

---

## When You'll See It

A function that doesn't explicitly `return` something returns `None` automatically:

```python
def greet(name):
    print(f"Hello, {name}")

result = greet("Alex")
print(result)       # None
```

Other examples:
- `list.append()` returns `None` (it modifies the list in place)
- A `dict.get(key)` returns `None` if the key isn't there

---

## Returning `None` On Purpose

It's common to return `None` to signal "no valid answer":

```python
def double_or_none(n):
    if n < 0:
        return None
    return n * 2

print(double_or_none(5))    # 10
print(double_or_none(-1))   # None
```

---

## Checking for `None`

Use `is` (not `==`) — it's clearer and slightly faster:

```python
result = double_or_none(-1)

if result is None:
    print("No valid result")
else:
    print("Result:", result)
```

`is not None` checks the opposite:

```python
if result is not None:
    print("Got something:", result)
```

---

## Practice

1. Write the `double_or_none(n)` function above. Call it with `5`, `0`, and `-3`. Print each result.

2. Write a function that takes a username and returns the user's age if you know it, or `None` otherwise:
   ```python
   def lookup_age(name):
       ages = {"Alice": 30, "Bob": 25}
       # use .get() or an if statement
   ```

3. Check the return value with `is None` and print a different message in each case.

---

## Question

What is `NoneType`, and how is the value `None` used in Python?

---

**Next up:** **Errors** — and how to handle them gracefully with `try`/`except`.
