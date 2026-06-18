---
title: Advanced Strings
type: lesson
---

# Advanced Strings

You already know how to make and slice strings. Python ships with dozens of string **methods** that transform, inspect, and search text. A few of them cover most of what you'll ever need.

---

## Transforming Methods

Methods that return a **new** string (the original is unchanged — strings are immutable).

| Method            | What it does                                  |
|-------------------|-----------------------------------------------|
| `s.upper()`       | All uppercase                                 |
| `s.lower()`       | All lowercase                                 |
| `s.title()`       | Title Case Each Word                          |
| `s.strip()`       | Remove whitespace from both ends              |
| `s.replace(a, b)` | Replace every `a` with `b`                    |
| `s.split()`       | Split into a list on whitespace               |
| `s.split(",")`    | Split on a specific separator                 |
| `"-".join(list)`  | Glue a list of strings together with `"-"`    |

```python
sentence = "Hello world!"

s = sentence.replace(" ", "_")
print(s)                # Hello_world!

s_upper = s.upper()
print(s_upper)          # HELLO_WORLD!
```

---

## Inspecting Methods

Methods that **return a boolean** or a number — they ask a question about the string.

| Method                | What it returns                              |
|-----------------------|----------------------------------------------|
| `s.startswith("Hi")`  | `True` if `s` starts with `"Hi"`             |
| `s.endswith(".py")`   | `True` if `s` ends with `".py"`              |
| `s.count("a")`        | How many times `"a"` appears                 |
| `s.find("x")`         | Index of first `"x"` (`-1` if not found)     |
| `s.isalpha()`         | `True` if every character is a letter        |
| `s.isdigit()`         | `True` if every character is a digit         |

```python
s_upper = "HELLO_WORLD!"
print(s_upper.startswith("HEL"))    # True
print(s_upper.count("L"))           # 3
print(s_upper.find("WORLD"))        # 6
```

---

## Checking for a Vowel

```python
s = "Apple"
print("Starts with vowel:", s[0].upper() in "AEIOU")    # True
```

`in` works on strings the same way it works on lists.

---

## Practice

1. Type a favourite phrase into a variable `sentence`.

2. Replace spaces with underscores; assign the result to `s` and print it.

3. Convert `s` to uppercase as `s_upper`. Print it.

4. Print whether `s_upper` starts with a vowel.

5. Use `startswith()` to check whether the first three letters of `s_upper` match the first three letters of your original phrase (uppercased).

6. **Experiment:** try `.count()` and `.find()` on your string. What do they return?

---

## Question

Which string methods did you use, and what does each one accomplish?

---

**Next up:** **String Formatting** — making f-strings and `.format()` do the work for you.
