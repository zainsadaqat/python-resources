This is where I would introduce the single most important idea in OOP.

Not `class`.

Not `self`.

Not `__init__`.

I would introduce **the Blueprint**.

---

# Lesson 2 — Blueprint vs Object

Start with a question.

> Imagine a construction company builds houses.

Do they build every house from memory?

No.

They first create a **blueprint**.

```text
           Blueprint

        ┌──────────────┐
        │   House Plan │
        │              │
        │ 2 Bedrooms   │
        │ 1 Kitchen    │
        │ 1 Garage     │
        └──────────────┘
```

That blueprint is **not** a house.

Nobody can live inside it.

It simply describes what every house should look like.

---

Now imagine the builder constructs three houses.

```text
Blueprint
      │
      │
      ├────────► House #1
      │
      ├────────► House #2
      │
      └────────► House #3
```

Question Marko:

> How many blueprints exist?

One.

> How many houses exist?

Three.

---

## Connect this to programming

Suppose we're building a library system.

How many books do we have?

Maybe

```text
25,000 books
```

Do we write

```python
book1 = {...}

book2 = {...}

book3 = {...}
```

25,000 times?

Of course not.

We create one blueprint.

That blueprint says:

> Every book should have

```text
Title

Author

ISBN

Copies
```

That's exactly what a **class** is.

A class is a blueprint.

---

# The most common misconception

Ask him:

> Is a class an object?

No.

A class is the description.

An object is the real thing.

Exactly like

```text
Blueprint ≠ House
```

Similarly,

```text
Book Class ≠ Book Object
```

---

# Real-world examples

## Cookie cutter

```text
Cookie Cutter
```

↓

Makes

```text
🍪 🍪 🍪 🍪 🍪
```

The cutter is reused.

The cookies are individual objects.

---

## Stamp

One stamp.

Thousands of impressions.

---

## Ice cube tray

One tray.

Twenty ice cubes.

---

## School

One student registration form.

Thousands of students.

The form isn't a student.

It's a template.

---

# Memory

This is where I usually draw memory.

Suppose we eventually write

```python
book1 = Book(...)
```

Don't explain syntax yet.

Instead explain what happens conceptually.

Memory:

```text
Book Blueprint

        │

        ▼

book1 ─────────► Object A

book2 ─────────► Object B

book3 ─────────► Object C
```

Notice something.

Each object stores different information.

```text
Book 1

Title:
Clean Code

Copies:
5
```

```text
Book 2

Title:
Atomic Habits

Copies:
8
```

```text
Book 3

Title:
Python Crash Course

Copies:
2
```

One blueprint.

Many independent objects.

---

# Ask an important question

Suppose I change

```text
Book 1

Copies

5

↓

4
```

Does Book 2 change?

No.

Each object owns its own data.

The blueprint doesn't store copies.

The object does.

---

# Compare with dictionaries

Current project:

```python
book1 = {
    ...
}

book2 = {
    ...
}
```

Question:

Where did these dictionaries come from?

We invented the structure ourselves.

Every time.

OOP says:

Let's define that structure once.

Then create objects from it.

---

# The factory analogy

Imagine Toyota.

Toyota doesn't build one car.

Toyota designs a model.

```text
Toyota Corolla
```

Then manufactures

```text
Car #1

Car #2

Car #3

...

Car #5,000,000
```

Every Corolla follows the same blueprint.

Yet each one has

* different owner
* different mileage
* different fuel
* different scratches

Same blueprint.

Different state.

---

# Why is this useful?

Suppose tomorrow we decide

Every book should also have

```text
Publisher
```

Without a blueprint

Every programmer has to remember

```python
book = {
    ...
    "publisher": ...
}
```

everywhere.

With a blueprint

We update the blueprint once.

Every future book automatically follows it.

---

# Homework

Ask Marko to identify the following.

## Which is the blueprint?

Which is the object?

Example 1

```text
Architectural drawing

House
```

---

Example 2

```text
Cookie cutter

Cookie
```

---

Example 3

```text
Car design

Toyota Corolla with registration ABC-123
```

---

Example 4

```text
Student admission form

Ali
```

---

Example 5

```text
Book definition

Clean Code
```

---

# Don't teach `class` yet

At the end of the lesson ask:

> If Python wanted to create a blueprint for books, what keyword do you think the language designers might have introduced?

Most students naturally answer:

> Maybe something like...

```text
Book
```

or

```text
Template
```

That's the perfect moment to reveal:

```python
class Book:
```

Not as new syntax.

As the natural way Python lets us define a blueprint.

This approach means that when Marko finally sees:

```python
class Book:
```

he'll already understand *why* it exists. The syntax becomes the easy part because the mental model is already in place.
