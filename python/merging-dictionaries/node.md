---
title: Merging Dictionaries
type: lesson
---

# Merging Dictionaries

Sometimes you have two dictionaries with related data and you want one combined dict. Python gives you a clean way to do this with the `**` unpacking syntax.

---

## The `**` Unpack Merge

```python
d1 = {'x': 1, 'y': 2}
d2 = {'y': 3, 'z': 4}

d = {**d1, **d2}
print(d)
# {'x': 1, 'y': 3, 'z': 4}
```

Read `**d1, **d2` as "spread every key/value of `d1`, then every key/value of `d2`, into a new dict."

---

## What Happens to Overlapping Keys?

Both `d1` and `d2` have a `'y'`. The **later** one (`d2`) wins because it's spread in second.

```python
d1 = {'y': 2}
d2 = {'y': 3}
print({**d1, **d2})     # {'y': 3}
```

If you flip the order, the answer flips too:

```python
print({**d2, **d1})     # {'y': 2}
```

---

## The `|` Operator (Python 3.9+)

A newer, even shorter syntax:

```python
d = d1 | d2
print(d)        # {'x': 1, 'y': 3, 'z': 4}
```

Both styles do the same thing — pick whichever is clearer.

---

## After Merging

You can mutate the merged dict like any other:

```python
d['x'] = 42         # update existing key
d['w'] = 99         # add a new key
print(d)
```

---

## Practice

1. Create two dictionaries:
   ```python
   d1 = {'x': 1, 'y': 2}
   d2 = {'y': 3, 'z': 4}
   ```

2. Merge them with `{**d1, **d2}` (or `d1 | d2`) into `d`.

3. Update a value (`d['x'] = 42`) and print.

4. Add a new value (`d['w'] = 99`) and print.

5. **Reflect:** what value does `d['y']` end up with? Why?

---

## Question

When both dictionaries share a key, which value wins, and why?

---

**Next up:** **Advanced Strings** — methods for transforming and inspecting text.
