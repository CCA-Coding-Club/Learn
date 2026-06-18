---
title: Data Types
type: lesson
---

# Data Types

Every value in Python belongs to a **type**. Knowing what type a value has tells Python what operations are legal on it — you can add two `int`s, but you can't add an `int` and a `str` without converting first.

---

## The Four You'll See Everywhere

| Type    | What it stores         | Examples                     |
|---------|------------------------|------------------------------|
| `int`   | Whole numbers          | `5`, `-3`, `42`              |
| `float` | Decimal numbers        | `3.14`, `-0.001`, `2.0`      |
| `str`   | Text (strings)         | `"hello"`, `'Python'`        |
| `bool`  | Truth values           | `True`, `False`              |

---

## Checking a Type

Use the built-in `type()` function:

```python
print(type(12))      # <class 'int'>
print(type(12.0))    # <class 'float'>
print(type('12'))    # <class 'str'>
print(type(True))    # <class 'bool'>
```

`'12'` (with quotes) is **not** the same as `12`. The quotes make it text.

---

## Converting Between Types

Python lets you convert with the type's name as a function:

```python
x = 5
print(type(x))        # int

x = float(x)
print(x, type(x))     # 5.0  float

y = "42"
print(int(y) + 1)     # 43
```

Conversions that don't make sense raise an error:

```python
int("hello")          # ValueError
```

---

## Practice

1. Write the type of each value:
   - `12` → `int`
   - `12.0` → ?
   - `'12'` → ?
   - `True` → ?
   - `False` → ?

2. Identify the data type of each variable below (without running it):
   ```python
   x = 5
   y = 'hello'
   z = 2.5
   is_valid = False
   ```

3. **On your computer:** Create a variable `x = 7`, print its type, then reassign `x = float(x)` and print its type again. What changes?

---

## Questions

- Why does it matter what data type a variable holds?
- What happens if you try `"hello" + 5`? Try it in the interpreter and read the error message.

---

**Next up:** Learn how **variables** store and name these values.
