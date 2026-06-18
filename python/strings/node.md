---
title: Strings
type: lesson
---

# Strings

A **string** is a sequence of characters — text. Strings show up everywhere: user input, file contents, messages, names, you name it.

---

## Creating a String

Single or double quotes both work:

```python
a = 'hello'
b = "world"
```

Use whichever doesn't conflict with the contents:

```python
quote = "It's a great day."     # contains an apostrophe
title = 'She said "hi"'         # contains double quotes
```

---

## Basic Operations

### Concatenation with `+`

```python
first = "Sam"
last = "Lee"
full = first + " " + last
print(full)         # Sam Lee
```

### Repetition with `*`

```python
print("ha" * 3)     # hahaha
```

### Length with `len()`

```python
print(len("Python"))    # 6
```

### Indexing with `[ ]`

Characters are numbered from `0`:

```python
word = "Python"
print(word[0])      # P
print(word[1])      # y
print(word[-1])     # n   (negative counts from the end)
```

### Slicing

`word[start:end]` returns characters from `start` up to (but not including) `end`:

```python
word = "Python"
print(word[0:3])    # Pyt
print(word[:3])     # Pyt   (start defaults to 0)
print(word[3:])     # hon   (end defaults to length)
```

---

## Converting To and From Strings

```python
n = 42
s = str(n)          # "42"

s = "7"
n = int(s)          # 7
```

You'll do this a lot — `input()` always returns a string, even if the user types a number.

---

## Practice

1. Create a variable `greeting = "Hello, world!"`. Print its **length** and its **first character**.

2. Concatenate your first and last name with a space between them, then print the result.

3. Ask the user for their favorite color and print:
   ```
   Your favorite color is: [color]
   ```

4. Use slicing to print just the first three characters of `"Python"`.

---

## Questions

- What error do you get if you ask for `"Python"[20]`?
- How do you convert the integer `5` to the string `"5"`?

---

**Next up:** Put it all together in the **Challenge** to test what you've learned.
