---
title: Errors
type: lesson
---

# Errors

Errors are how Python tells you something went wrong. Learning to **read** error messages — and **handle** the ones you can predict — is one of the biggest jumps from beginner to confident programmer.

---

## Common Errors

| Error              | When it happens                                  |
|--------------------|--------------------------------------------------|
| `SyntaxError`      | Code can't even be parsed (typo, missing colon)  |
| `NameError`        | Used a variable that doesn't exist               |
| `TypeError`        | Wrong type for an operation (e.g., `"a" + 5`)    |
| `ValueError`       | Right type, wrong value (e.g., `int("hello")`)   |
| `IndexError`       | List/string index out of range                   |
| `KeyError`         | Dictionary key doesn't exist                     |
| `ZeroDivisionError`| Divided by zero                                  |
| `FileNotFoundError`| Tried to open a file that doesn't exist          |

### Triggering them on purpose

```python
my_list = [1, 2, 3]
print(my_list[10])      # IndexError

print(int("hello"))     # ValueError

print(10 / 0)           # ZeroDivisionError
```

---

## try / except

Wrap risky code in `try`, and catch the error with `except`:

```python
try:
    print(10 / 0)
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

The program **doesn't crash** — it runs the `except` block instead.

---

## Catching Multiple Errors

```python
try:
    value = int(input("Enter a number: "))
    print(100 / value)
except ValueError:
    print("That's not a number!")
except ZeroDivisionError:
    print("You can't divide by zero!")
```

Each `except` handles one specific error type. The matching one runs.

---

## Getting the Error Message

```python
try:
    int("hello")
except ValueError as e:
    print("Something went wrong:", e)
```

`as e` captures the exception object so you can read its message.

---

## `else` and `finally`

| Block       | Runs when                              |
|-------------|----------------------------------------|
| `try`       | Always — your risky code               |
| `except`    | Only if a matching error was raised    |
| `else`      | Only if **no** error was raised        |
| `finally`   | **Always**, error or not (cleanup)     |

```python
try:
    n = int(input("Number: "))
except ValueError:
    print("Bad input")
else:
    print("Got it:", n)
finally:
    print("Done.")
```

---

## Practice

1. Look up `IndexError`, `ValueError`, and `ZeroDivisionError` in the Python docs (or [docs.python.org/3/tutorial/errors.html](https://docs.python.org/3/tutorial/errors.html)). Trigger each one on purpose and read the error message.

2. Write code that handles **at least two** different error types gracefully:
   ```python
   try:
       print(int("abc"))
   except ValueError:
       print("That's not a number!")
   ```

3. Write a divider that asks for two numbers and handles both `ValueError` (non-numeric input) and `ZeroDivisionError` (dividing by zero).

---

## Question

What happens when your code hits an unhandled error? How does `try`/`except` change that?

---

**Next up:** **Stacks** — using a list as a Last-In, First-Out container.
