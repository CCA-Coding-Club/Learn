---
title: Conditionals
type: lesson
---

# Conditionals

Conditionals let your program take different actions depending on what's true. They turn straight-line scripts into things that can actually make decisions.

---

## if

The simplest form: do something only if a condition is true.

```python
age = 20
if age >= 18:
    print("You can vote.")
```

The **indentation** matters in Python. Everything indented under the `if` runs only when the condition is true.

---

## if / else

Run one block or the other:

```python
age = 15
if age >= 18:
    print("You can vote.")
else:
    print("Too young to vote.")
```

---

## if / elif / else

Check multiple conditions in order:

```python
score = 82
if score >= 90:
    print("Excellent")
elif score >= 70:
    print("Good")
else:
    print("Needs Improvement")
```

Python checks each condition top-to-bottom and runs the **first** one that's true. Once a branch runs, the rest are skipped.

---

## Comparison Refresher

| Operator | Meaning              |
|----------|----------------------|
| `==`     | Equal to             |
| `!=`     | Not equal to         |
| `>`      | Greater than         |
| `<`      | Less than            |
| `>=`     | Greater or equal     |
| `<=`     | Less or equal        |

---

## Practice

1. Write a program that checks if a person is old enough to vote (`age >= 18`) and prints an appropriate message either way.

2. Ask the user for a number, then print whether it's **negative**, **zero**, or **positive**:
   ```python
   n = int(input("Enter a number: "))
   # your if/elif/else here
   ```

3. Given a variable `score`, print:
   - `"Excellent"` if the score is **over 90**
   - `"Good"` if it's **between 70 and 90**
   - `"Needs Improvement"` otherwise

---

## Questions

- If two `elif` conditions are both true, which one runs?
- When does the `else` block run?

---

**Next up:** **Strings** — text values and the operations you can do with them.
