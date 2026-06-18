---
title: Lists
type: lesson
---

# Lists

A **list** is an ordered, changeable collection of values. Lists are the workhorse data structure of Python — you'll use them constantly to group related items together.

---

## Creating a List

Square brackets, comma-separated values:

```python
my_list = [10, 20, 30, 40]
empty = []
mixed = [1, "apple", [2, 3]]      # lists can hold any types
```

---

## Accessing Elements

Indexing starts at `0`. Negative indexes count from the end.

```python
my_list = [10, 20, 30, 40]
print(my_list[0])     # 10
print(my_list[2])     # 30
print(my_list[-1])    # 40   (last item)
```

Asking for an index that doesn't exist raises `IndexError`:

```python
print(my_list[10])    # IndexError: list index out of range
```

---

## Common List Methods

| Method            | What it does                                            |
|-------------------|---------------------------------------------------------|
| `append(x)`       | Adds `x` to the end                                     |
| `pop()`           | Removes and returns the last item                       |
| `pop(i)`          | Removes and returns item at index `i`                   |
| `remove(x)`       | Removes the **first** occurrence of value `x`           |
| `insert(i, x)`    | Inserts `x` at index `i`                                |
| `len(my_list)`    | Number of items in the list                             |
| `in`              | Check membership: `20 in my_list` → `True`              |

```python
my_list = [10, 20, 30, 40]
my_list.append(50)        # [10, 20, 30, 40, 50]
my_list.pop()             # returns 50, list is now [10, 20, 30, 40]
my_list.remove(20)        # [10, 30, 40]
print(len(my_list))       # 3
```

---

## Slicing

Same syntax as strings:

```python
nums = [1, 2, 3, 4, 5]
print(nums[1:4])      # [2, 3, 4]
print(nums[:2])       # [1, 2]
print(nums[-2:])      # [4, 5]
```

---

## Practice

1. Create a list with several elements of your choice. Print the whole list, then print individual elements by index.

2. **Cause an error on purpose:** try printing an index well past the end of your list. Read the error message.

3. Modify the list using `append()`, `pop()`, and `remove()`. Print the list after each step.

4. Create a list that contains a **mix of types** — numbers, strings, and a nested list. Try indexing into the nested list:
   ```python
   mixed = [1, "apple", [2, 3]]
   print(mixed[2][0])    # 2
   ```

---

## Question

What happens when you try to access an index that doesn't exist? What's the error called?

---

**Next up:** **Loops** — how to walk through a list and do something with each item.
