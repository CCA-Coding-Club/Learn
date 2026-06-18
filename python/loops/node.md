---
title: Loops
type: lesson
---

# Loops

Loops let you repeat work without rewriting code. Python has two main kinds: `for` (repeat for each item in a collection) and `while` (repeat until a condition becomes false).

---

## The `for` Loop

The most common loop. Walks through any collection — a list, a string, a range of numbers.

```python
for i in range(5):
    print(i)
```

Output:
```
0
1
2
3
4
```

`range(5)` produces `0, 1, 2, 3, 4` — five numbers, **not including** 5.

### Looping over a list

```python
my_list = [10, 20, 30, 40]
for item in my_list:
    print(item)
```

You don't need an index — Python hands you the item directly.

---

## The `while` Loop

Repeats as long as a condition is true.

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

> ⚠️ If the condition never becomes false, you have an **infinite loop**. Press `Ctrl+C` to stop a runaway program.

A common pattern — loop until the user types `'quit'`:

```python
user_input = ""
while user_input != "quit":
    user_input = input("Type something (or 'quit' to exit): ")
```

---

## Loops + Conditionals

Combining a loop with an `if` is where loops really earn their keep:

```python
my_list = [3, 6, 7, 12, 15, 22]
for num in my_list:
    if num % 2 == 0:
        print(num)        # prints only the even numbers
```

---

## `break` and `continue`

| Keyword    | What it does                                |
|------------|---------------------------------------------|
| `break`    | Exit the loop immediately                   |
| `continue` | Skip the rest of this iteration, keep going |

```python
for n in range(10):
    if n == 5:
        break             # stop completely
    if n % 2 == 0:
        continue          # skip even numbers
    print(n)              # prints 1, 3
```

---

## Practice

1. Write a `for` loop that prints each item in this list, one per line:
   ```python
   my_list = ["apple", "banana", "cherry"]
   ```

2. Loop through `range(1, 11)` and print only the **even** numbers.

3. Write a `while` loop that keeps asking the user for input until they type `"quit"`:
   ```python
   while True:
       txt = input("> ")
       if txt == "quit":
           break
   ```

---

## Question

How do you use a loop to process each item in a list?

---

**Next up:** **Functions** — packaging code so you can call it by name.
