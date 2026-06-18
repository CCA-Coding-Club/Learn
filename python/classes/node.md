---
title: Classes
type: lesson
---

# Classes

A **class** is a blueprint for your own custom type. It bundles related **data** (attributes) and **behaviour** (methods) into one object. Once you have a class, you can create as many objects ("instances") of it as you want.

---

## Defining a Class

```python
class Book:
    def __init__(self, title):
        self.title = title

    def display(self):
        print(f"Title: {self.title}")
```

What's going on:

- `class Book:` — start defining a new type called `Book`.
- `__init__` — the **constructor**, called automatically when you create an instance. It sets up the object's attributes.
- `self` — the instance itself. Every method's first parameter is `self`.
- `self.title = title` — stores the title on the object.
- `display(self)` — a method (a function that belongs to the class).

---

## Creating and Using an Object

```python
mybook = Book("Python 101")
mybook.display()        # Title: Python 101

other = Book("Algorithms")
other.display()         # Title: Algorithms
```

`Book("Python 101")` runs `__init__` with `title="Python 101"`. `mybook` is a `Book` instance.

---

## Multiple Attributes

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        print(f"Hi, I am {self.name} and I am {self.age} years old.")

p = Person("Sam", 15)
p.introduce()       # Hi, I am Sam and I am 15 years old.
```

---

## Methods That Return Values

A method doesn't have to print — it can return a value just like any function.

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

rect = Rectangle(3, 4)
print(rect.area())      # 12
```

---

## When To Use a Class

A class earns its keep when:

- You have several things that **belong together** (a player has health, score, position, inventory...)
- You'll be creating **many similar** instances (every enemy in a game is an `Enemy`)
- The data needs **behaviour** attached to it (a `BankAccount` knows how to deposit and withdraw)

For one-off scripts, a dict or tuple is often enough.

---

## Practice

### 1. `Book`

A class with a `title` attribute and a `display()` method that prints `"Title: [title]"`.

```python
class Book:
    def __init__(self, title):
        self.title = title

    def display(self):
        print(f"Title: {self.title}")

mybook = Book("Python 101")
mybook.display()
```

### 2. `Person`

`name`, `age`, and an `introduce()` method that prints `"Hi, I am [name] and I am [age] years old."`

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        print(f"Hi, I am {self.name} and I am {self.age} years old.")

p = Person("Sam", 15)
p.introduce()
```

### 3. `Rectangle`

`width`, `height`, and an `area()` method that **returns** `width * height`.

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

rect = Rectangle(3, 4)
print(rect.area())      # 12
```

---

## Question

What's the role of `self` in a class method?

---

**Next up:** Combine everything in the **Challenge**.
