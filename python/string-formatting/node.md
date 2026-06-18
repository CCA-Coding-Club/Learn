---
title: String Formatting
type: lesson
---

# String Formatting

There are three ways to plug variables into a string in Python. **f-strings** are the modern, readable default; `.format()` is the older but still useful version; `%`-style is the oldest and rarely worth using today.

---

## f-strings (Recommended)

Put an `f` in front of the string and embed variables in `{ ... }`:

```python
first = "Taylor"
last = "Swift"
age = 30

print(f"{last}-{first}")
# Swift-Taylor

print(f"{last}-{first}, Age: {age}")
# Swift-Taylor, Age: 30
```

You can put **expressions** inside the braces, not just variables:

```python
print(f"Next year you'll be {age + 1}")
print(f"{first.upper()} says hi")
```

---

## Format Specifiers

After a colon inside the braces, you can control how the value is shown:

| Spec      | Example output for `pi = 3.14159` |
|-----------|-----------------------------------|
| `{pi}`    | `3.14159`                         |
| `{pi:.2f}`| `3.14`        (2 decimal places)  |
| `{pi:10}` | `   3.14159`  (10 wide, right-aligned) |
| `{pi:<10}`| `3.14159   `  (left-aligned)      |

```python
pi = 3.14159
print(f"Pi is about {pi:.2f}")
# Pi is about 3.14
```

---

## The `.format()` Method

The older but still common style. Positional placeholders:

```python
x, y, z = "Sam", "Sam's", "color"
print("{0} is {1} favorite {2}.".format(x, y, z))
# Sam is Sam's favorite color.
```

Named placeholders are clearer for longer templates:

```python
print("{name} is {age} years old.".format(name="Alex", age=20))
```

---

## When to Use Each

| Style       | When it shines                              |
|-------------|---------------------------------------------|
| f-string    | Most code — readable, inline, fast          |
| `.format()` | Templates with placeholders defined elsewhere |
| `%`-style   | Legacy code; avoid in new code              |

---

## Practice

1. Set `first = "Taylor"` and `last = "Swift"`. Print `{last}-{first}` using an f-string.

2. Add `age = 30` and print `Swift-Taylor, Age: 30`.

3. Add `color = "blue"` and print `Swift, Taylor: Favorite color is blue`.

4. Try the `.format()` style:
   ```python
   print("{0} is {1} favorite {2}.".format("blue", "Sam's", "color"))
   ```

5. **Experiment:** print a float to 2 decimal places using `{:.2f}`.

---

## Question

What advantages do f-strings offer compared to `%`-formatting or `.format()`?

---

**Next up:** **List Comprehensions** — a one-line way to build lists from loops.
