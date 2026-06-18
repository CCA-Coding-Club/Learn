---
title: Functions in Depth
type: lesson
---

# Functions in Depth

You already know how to define and call a function. This lesson goes one step further — designing functions that take collections, return useful values, and combine cleanly with comprehensions.

---

## Functions That Take Collections

A parameter can be any type, including a list:

```python
def add_ten(numbers):
    return [n + 10 for n in numbers]

print(add_ten([1, 2, 3]))    # [11, 12, 13]
```

Notice: `add_ten` doesn't modify its input — it returns a **new** list. That's almost always the safer design.

---

## Functions That Return Booleans

A function whose job is to answer a yes/no question should return `True` or `False`:

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

print(is_prime(7))      # True
print(is_prime(8))      # False
```

A common convention: name boolean functions `is_...` or `has_...`.

---

## Multiple Returns, One Function

You can `return` from many places in a function. The first one that runs wins — the rest never execute.

In `is_prime` above, the function exits **immediately** the first time it finds a divisor. That's called an **early return** and keeps code flat and readable.

---

## Returning Multiple Values

A function can return a tuple — and the caller can unpack it:

```python
def min_max(numbers):
    return min(numbers), max(numbers)

low, high = min_max([3, 1, 4, 1, 5, 9, 2, 6])
print(low, high)        # 1 9
```

---

## Practice

### 1. `greet(name)`

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alex")
```

### 2. `add_ten(numbers)`

Takes a list of numbers, returns a new list with each number increased by 10.

```python
def add_ten(numbers):
    return [n + 10 for n in numbers]

print(add_ten([1, 2, 3]))    # [11, 12, 13]
```

### 3. `is_prime(n)`

Returns `True` if `n` is prime, `False` otherwise.

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

print(is_prime(7))      # True
print(is_prime(8))      # False
```

---

## Question

What's the difference between a function that **prints** and a function that **returns**? When would you choose each?

---

**Next up:** **Lambda** — tiny anonymous functions for one-line jobs.
