---
title: Variables
type: lesson
---

# Variables

A **variable** is a name that points to a value. Python figures out the type automatically — you don't declare it like you would in Java or C.

---

## Creating a Variable

```python
age = 14
favorite_color = "blue"
likes_pizza = True
```

The `=` is the **assignment** operator. The name on the left now refers to the value on the right.

---

## Naming Rules

| Rule                                  | Example                |
|---------------------------------------|------------------------|
| Start with a letter or underscore     | `name`, `_temp`        |
| Contains letters, numbers, underscores| `score1`, `user_age`   |
| Case-sensitive                        | `Name` ≠ `name`        |
| Can't use Python keywords             | not `for`, `if`, `True`|

By convention, Python uses **snake_case** (lowercase with underscores), not `camelCase`.

```python
# Good
first_name = "Sam"
total_score = 100

# Avoid
firstName = "Sam"
TotalScore = 100
```

---

## Reassignment

Assigning a new value to the same name simply replaces it:

```python
city = "Toronto"
print(city)        # Toronto

city = "Vancouver"
print(city)        # Vancouver
```

The old value isn't kept anywhere — it's gone.

You can even reassign with a completely different type:

```python
x = 5
x = "five"
print(x)           # five
```

Python won't stop you, but it's usually a sign of confused code.

---

## Practice

Create a brand-new Python file and try each of these:

1. Create variables for your **age**, **favorite color**, and **whether you like pizza** (use a boolean).
2. Assign a string to a variable `city`, print it, change it to a new city, then print again.
3. Try assigning a number to `x`, then reassign `x` to a string. Print `type(x)` before and after.

---

## Questions

- What happens to the original value when you reassign a variable?
- Can a variable name contain numbers? (Hint: try `score1 = 10` and `1score = 10` and see which works.)

---

**Next up:** **Terminal I/O** — talking to the user with `input()` and `print()`.
