---
title: Lambda Functions
type: lesson
---

# Lambda Functions

A **lambda** is a tiny, one-line, anonymous function. It does the same job as a regular `def` function, but you can write it inline without giving it a name. Lambdas are perfect for short transformations passed to `map`, `filter`, and `sorted`.

---

## Shape

```text
lambda parameters: expression
```

The expression is whatever the function returns. There's no `return` keyword — the expression itself is the return value.

```python
square = lambda x: x * x
print(square(5))        # 25
```

Same as:

```python
def square(x):
    return x * x
```

Lambdas shine when you're passing a function as an argument and don't need to give it a name.

---

## `map` — Transform Every Item

`map(fn, iterable)` applies `fn` to every item.

```python
numbers = [2, 4, 6]
result = list(map(lambda x: x * 3, numbers))
print(result)           # [6, 12, 18]
```

A list comprehension would work too — `[x * 3 for x in numbers]`. Many Pythonistas prefer the comprehension for simple transforms.

---

## `filter` — Keep Only the Items That Match

`filter(fn, iterable)` keeps the items where `fn` returns `True`.

```python
numbers = [3, 6, 9, 2, 8]
filtered = list(filter(lambda x: x > 5, numbers))
print(filtered)         # [6, 9, 8]
```

Equivalent comprehension: `[x for x in numbers if x > 5]`.

---

## `sorted` with a Key

This is where lambdas really pay off. Sort a list of tuples by their **second** value:

```python
tuples = [(1, 3), (2, 2), (4, 1)]
sorted_tuples = sorted(tuples, key=lambda x: x[1])
print(sorted_tuples)
# [(4, 1), (2, 2), (1, 3)]
```

Without the lambda you'd have to define a whole helper function — for a one-time use, that's overkill.

### Sort by length

```python
words = ["banana", "kiwi", "apple"]
print(sorted(words, key=lambda w: len(w)))
# ['kiwi', 'apple', 'banana']
```

---

## When *Not* To Use a Lambda

If the function does more than fit on one line, or if it has multiple statements, write a regular `def`. Lambdas are only for tiny things.

---

## Practice

1. Use `map` with a lambda to multiply every number in `[2, 4, 6]` by 3.

2. Use `filter` with a lambda to select every number greater than 5 from `[3, 6, 9, 2, 8]`.

3. Sort the list of tuples `[(1, 3), (2, 2), (4, 1)]` by the **second** value of each tuple using `sorted(..., key=lambda x: x[1])`.

---

## Question

When does a lambda make code clearer than a regular `def`, and when does it make code worse?

---

**Next up:** **Files** — saving and loading data from disk.
