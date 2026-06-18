---
title: Terminal I/O
type: lesson
---

# Terminal I/O

`input()` and `print()` are how your program **talks to the user** in the terminal. Mastering them — and remembering that `input()` always gives you a string — keeps a whole class of bugs out of your code.

---

## `input()`

`input()` pauses the program, waits for the user to type something and press Enter, then returns whatever they typed as a **string**.

```python
name = input("What is your name? ")
print(f"Hello {name}!")
```

The string in `input(...)` is the **prompt** — what the user sees before they type.

---

## Always a String

Even when the user types a number, you get back a string:

```python
n = input("Enter a number: ")
print(type(n))      # <class 'str'>
```

To do math, you need to convert:

```python
n = int(input("Enter a number: "))
print(n + 1)
```

| Convert to | Use         |
|------------|-------------|
| Integer    | `int(...)`  |
| Decimal    | `float(...)`|
| Bool       | not directly — write your own check |

---

## Handling Bad Input

`int()` raises `ValueError` if the string isn't a number:

```python
try:
    age = int(input("Age? "))
except ValueError:
    print("Please type a whole number.")
```

In real programs, wrapping `input()` parsing in `try`/`except` is the difference between a friendly tool and one that crashes.

---

## `print()` Tricks

### Separator and end

```python
print("a", "b", "c")              # a b c
print("a", "b", "c", sep="-")     # a-b-c
print("hi", end="")               # no newline after
print("there")                    # hithere on the same line
```

### Combining with f-strings

```python
name = "Sam"
age = 15
print(f"Hello {name}, you are {age} years old.")
```

---

## Practice

### 1. Favourite Food

```python
food = input("What is your favorite food? ")
print(f"Yum! I like {food}, too.")
```

### 2. Sum Two Numbers

```python
a = int(input("Enter a number: "))
b = int(input("Enter another number: "))
print("The sum is:", a + b)
```

### 3. Name and Age

```python
name = input("What is your name? ")
age = input("How old are you? ")
print(f"Hello {name}, you are {age} years old.")
```

---

## Question

What type does `input()` always return, and what do you have to do to use it as a number?

---

**Next up:** **Boolean Logic** — combining `True`/`False` values to make decisions.
