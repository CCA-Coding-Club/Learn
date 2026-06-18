---
title: Boolean Logic
type: lesson
---

# Boolean Logic

Booleans (`True` and `False`) are how programs make decisions. Almost every `if` statement boils down to a boolean expression.

---

## True and False

`True` and `False` are **keywords** — capital T, capital F, no quotes.

```python
is_raining = True
has_umbrella = False
```

`true` (lowercase) is **not** a boolean — it's a name Python will try to look up and fail to find.

---

## Comparison Operators

These produce booleans:

| Operator | Meaning              | Example          | Result |
|----------|----------------------|------------------|--------|
| `==`     | Equal to             | `3 == 3`         | `True` |
| `!=`     | Not equal to         | `3 != 4`         | `True` |
| `>`      | Greater than         | `5 > 2`          | `True` |
| `<`      | Less than            | `5 < 2`          | `False`|
| `>=`     | Greater or equal     | `5 >= 5`         | `True` |
| `<=`     | Less or equal        | `4 <= 3`         | `False`|

> ⚠️ `=` assigns, `==` compares. Mixing them up is the #1 beginner bug.

---

## Logical Operators

Combine booleans with `and`, `or`, `not`:

```python
print(True and False)     # False
print(True or False)      # True
print(not False)          # True
```

| Operator | True when                          |
|----------|------------------------------------|
| `and`    | **Both** sides are True            |
| `or`     | **At least one** side is True      |
| `not`    | The value is False                 |

---

## Combining Comparisons

You can chain comparisons with `and`/`or`:

```python
age = 20
has_id = True

can_enter = age >= 18 and has_id
print(can_enter)        # True
```

```python
n = 6
is_positive_and_even = n > 0 and n % 2 == 0
print(is_positive_and_even)   # True
```

---

## Practice

1. Evaluate each expression (predict, then run it):
   - `True and False` → ?
   - `not False` → ?
   - `True or False` → ?
   - `(3 > 2) and (5 < 10)` → ?
   - `(3 == 4) or (1 != 2)` → ?

2. Write a single expression that's `True` when a number is **both positive and even**.

3. What does `not True` return?

---

## Questions

- Why is boolean logic essential to programming?
- Give a real-world example where you'd use `or` (e.g., "show discount if it's the user's birthday **or** they have a coupon").

---

**Next up:** **Conditionals** — using booleans to actually control what your program does.
