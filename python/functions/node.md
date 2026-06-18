---
title: Functions
type: lesson
---

# Functions

A **function** is a named block of reusable code. Defining a function once and calling it many times is how you stop repeating yourself and start building real programs.

---

## Defining a Function

```python
def greet(name):
    print(f"Hello, {name}!")
```

Pieces:
- `def` — the keyword that starts a function definition
- `greet` — the function's name
- `(name)` — the **parameter** the function accepts
- `:` and the indented body — what runs when you call it

---

## Calling a Function

```python
greet("Sam")        # Hello, Sam!
greet("Alex")       # Hello, Alex!
```

You can call the same function over and over with different inputs.

---

## Returning a Value

`print` shows something on screen; `return` hands a value back to whoever called the function. They are **not** the same.

```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)       # 5
print(add(10, 4))   # 14
```

A function with no `return` returns `None` automatically.

---

## Parameters vs Arguments

- **Parameter** — the name in the function definition (`name`, `a`, `b`).
- **Argument** — the actual value you pass when calling (`"Sam"`, `2`, `3`).

You can have multiple parameters separated by commas.

---

## Default Values

Give a parameter a default so callers can leave it out:

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Sam")                  # Hello, Sam!
greet("Sam", "Hi")            # Hi, Sam!
```

---

## Combining Functions with Lists and Loops

```python
def square(x):
    return x * x

numbers = [1, 2, 3, 4]
for n in numbers:
    print(square(n))          # 1, 4, 9, 16
```

This is the building block of clean Python: small functions doing one thing, called from loops.

---

## Practice

1. Write a `greet(name)` function. Call it with three different names.

2. Write `add(a, b)` that **returns** the sum (don't `print` — return). Use it in `print(add(2, 3))`.

3. Write `square(x)` that returns `x * x`. Use it inside a `for` loop to print the squares of `[1, 2, 3, 4, 5]`.

4. Write a function `is_positive(n)` that returns `True` if `n > 0`, else `False`. Test it on a few numbers.

---

## Question

What are the steps to define and use a function in Python? (Hint: define, then call.)

---

**Next up:** **NoneType** — the special "no value" value and how to handle it.
