# Object Oriented Programming Lesson-01 in Python

I would avoid starting with `class`, `object`, `self`, or `__init__`.

The first lesson should answer one question:

> **Why did programmers invent Object-Oriented Programming?**

If that question isn't answered first, the rest feels like memorizing syntax.

---

# Lesson 1 – Why OOP Exists

## Imagine your room

Look around your room.

You might see:

* A laptop
* A phone
* A water bottle
* A chair
* A keyboard

These are all **entities**.

## What is an entity?

An **entity** is simply **something that exists and has its own identity.**

Examples:

* A person
* A book
* A library member
* A bank account
* A student
* A football
* A car

In programming we often need to represent real-world entities.

---

# Every entity has two things

## 1. Information (State)

Take a phone.

It has:

```
Brand: Apple

Model: iPhone 15

Battery: 82%

Storage: 256GB

Color: Black
```

These describe the phone.

They are called **attributes** (or properties).

---

## 2. Actions (Behavior)

A phone can:

* Call someone
* Send a message
* Charge
* Play music
* Take a picture

These are behaviors.

Notice something?

A phone is not just information.

It can also **do things**.

---

# Another example

Take yourself.

You have information.

```
Name

Age

Height

Weight

Occupation
```

You also have behaviors.

```
Walk

Eat

Teach

Sleep

Code
```

Everything around us follows this pattern.

---

# Let's relate this to our project

What is a book?

Information:

```
Title

Author

ISBN

Copies
```

Behavior:

```
Borrow

Return

Display information
```

What about a member?

Information:

```
Name

Email

Phone

Maximum books allowed
```

Behavior:

```
Borrow a book

Return a book

View borrowed books
```

Notice how naturally this maps to real life.

---

# How have we represented a book so far?

Using a dictionary.

```python
book = {
    "title": "Clean Code",
    "author": "Robert C. Martin",
    "isbn": "978...",
    "copies": 5
}
```

This works.

So why change it?

---

# The problem with dictionaries

Imagine Amazon stores

```
50 million books
```

Every programmer must remember

```
title

author

isbn

copies
```

What if someone writes

```python
book["copy"]
```

instead of

```python
book["copies"]
```

Python won't help.

Or

```python
book = {
    "title": "...",
    "isbn": "..."
}
```

Oops.

The author is missing.

Nothing prevents this.

---

# Another problem

Suppose we have these functions.

```python
display_book(book)

borrow_book(book)

return_book(book)

update_book(book)
```

Ask Marko:

**What do all these functions have in common?**

They all work with books.

They're related.

Yet they're scattered throughout the project.

---

# Imagine a library

Instead of this.

```
Books

Functions

Books

Functions

Books

Functions
```

Wouldn't it be nicer if everything related to a book stayed together?

That's one of the reasons OOP exists.

---

# A real-world analogy

Imagine buying a washing machine.

Do you receive

```
The machine

A separate box containing all its buttons

Another box containing the washing program

Another box containing the power button
```

No.

Everything belongs together.

The machine contains both

* information
* behavior

Objects work the same way.

---

# Think about your phone

You don't say

```
charge(phone)

take_picture(phone)

play_music(phone)
```

Instead you naturally think

```
phone.charge()

phone.take_picture()

phone.play_music()
```

That's exactly how OOP thinks.

---

# Why OOP was invented

As software became larger,

people noticed code becoming

```
Huge

Messy

Hard to understand

Hard to reuse

Hard to maintain
```

Programmers needed a better way to organize related data and behavior.

Object-Oriented Programming was one solution.

---

# Advantages of OOP

### Better organization

Everything related to a book stays together.

---

### Easier maintenance

Need to change how borrowing works?

You know exactly where to look.

---

### Easier teamwork

One developer works on Books.

Another works on Members.

Another works on Borrowing.

---

### Reusability

You can reuse the same class many times.

---

### Models the real world

Books.

Cars.

Students.

Employees.

Animals.

These naturally become objects.

---

# Disadvantages

OOP isn't always the best choice.

---

### More code

A simple script becomes

```
Classes

Methods

Objects
```

Sometimes that's unnecessary.

---

### More concepts

Beginners must learn

```
Objects

Classes

Methods

Constructors

self

Inheritance

Polymorphism
```

That's a lot.

---

### Overengineering

Some people create

```
12 classes

40 methods

8 files
```

for a program that prints

```
Hello World
```

That's bad design.

---

# When should we use OOP?

When you're building software that represents things.

Examples:

```
Library Management System

Banking System

Hospital Management

School Management

E-commerce

Games

Social Media

Inventory System
```

Notice something?

All these systems have entities.

---

# When should we NOT use OOP?

Simple scripts.

Examples:

```
Rename 100 files

Convert CSV to JSON

Calculate salary

Web scraping

Read Excel

Automation

Data analysis
```

Often a few functions are enough.

---

# One thing beginners misunderstand

Many think

> OOP is better than procedural programming.

That's false.

OOP is **another tool**.

Just like:

* Hammer
* Screwdriver
* Wrench

You don't always use a hammer.

Likewise, you don't always use OOP.

---

# Connect it back to Marko's project

Ask him:

> We currently have

```python
display_book(book)

borrow_book(book)

update_book(book)

search_book(...)
```

Do these functions belong to books?

Most students answer:

**Yes.**

Then ask:

> Instead of passing the book into every function, wouldn't it be nice if the book already knew how to display itself or update its own information?

That's the moment students begin to appreciate OOP before seeing a single line of OOP syntax.

---

## Homework

Choose **five real-world entities** around your house.

For each one, identify:

1. **State (Attributes):** What information describes it?
2. **Behavior (Methods):** What actions can it perform?

Example:

```
Entity: Bicycle

Attributes:
- Brand
- Color
- Number of gears
- Current speed

Behaviors:
- Ride
- Brake
- Change gear
- Ring bell
```

The goal of this lesson is not to learn `class` syntax. The goal is to train the habit of seeing the world as entities with state and behavior. Once that way of thinking becomes natural, writing `class Book:` feels like the obvious next step rather than a new programming trick.
