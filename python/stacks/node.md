---
title: Stacks
type: lesson
---

# Stacks

A **stack** is a Last-In, First-Out (LIFO) collection — the last item you put in is the first one you take out. Think of a stack of plates: you add and remove from the top.

Python doesn't have a separate `Stack` type. You just use a list.

---

## The Two Operations

| Stack op | Python list method | What it does                  |
|----------|-------------------|-------------------------------|
| Push     | `.append(x)`      | Add `x` to the top            |
| Pop      | `.pop()`          | Remove and return the top item|

```python
stack = []

stack.append(1)     # stack: [1]
stack.append(2)     # stack: [1, 2]
stack.append(3)     # stack: [1, 2, 3]

top = stack.pop()   # top = 3, stack: [1, 2]
print(top)
print(stack)
```

The top of the stack is the **end** of the list — index `-1`.

---

## Peeking

To look at the top without removing it:

```python
print(stack[-1])
```

---

## Why Stacks Are Useful

Lots of real problems have a LIFO shape:

- **Browser back button** — visited pages stack up; back pops the latest one.
- **Undo history** — newest action goes on top, undo pops it off.
- **Function call stack** — Python itself uses one to track which function called which.
- **Reversing things** — push characters in, pop them out, you get the reverse.

---

## Example: Reverse a Word

```python
word = "python"
stack = list(word)        # ['p', 'y', 't', 'h', 'o', 'n']

reversed_word = ""
while stack:              # loops while stack is non-empty
    reversed_word += stack.pop()

print(reversed_word)      # nohtyp
```

The `while stack:` trick — an empty list is "falsy," so the loop stops automatically when everything's been popped.

---

## Practice

1. Create an empty stack. Push three numbers, then pop one. Print the stack after each step.

2. Use a stack to reverse a word the user types in:
   ```python
   word = input("Enter a word: ")
   # build a stack from word, pop everything off into a new string
   ```

3. Print the stack after each push and pop so you can see how it changes.

---

## Question

How do you add or remove elements from a stack using a list?

---

**Next up:** Test everything from Worksheet 2 in the **Challenge**.
