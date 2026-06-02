# Functions in Python

## To become Top 1% in Python functions, you need a layered understanding

Basic syntax

Parameters and arguments

Return values

Scope and namespaces

First-class functions

Closures

Decorators

Higher-order functions

Functional patterns

Introspection

Signature manipulation

Async functions

Metaprogramming patterns

Framework-level architecture using functions

## Exercise 1 — Functions Are Objects

### Goal

Understand that functions in Python are values, not just reusable code blocks.

### Task

Predict the output of this code WITHOUT running it.

```py
def greet():
    return "hello"

x = greet

print(greet)
print(x)
print(greet())
print(x())
print(greet is x)
```

Then answer:

#### 1. What is stored inside x?

#### 2. Difference between greet and greet()

#### 3. Why does greet is x return what it returns?

#### 4. What does this reveal about Python functions internally?

Expected output:

```python
<function greet at 0x...>
<function greet at 0x...>
hello
hello
True
```

Breakdown:

### 1. What is stored inside `x`?

`x` stores the actual function object reference.

In Python, functions are first-class objects. The name `greet` is just a label pointing to a function object in memory.

This means:

```python
x = greet
```

does NOT copy the function.

Both names now point to the SAME function object.

Memory model:

```python
greet ─────┐
           ├──> function object
x     ─────┘
```

---

### 2. Difference between `greet` and `greet()`

| Expression | Meaning                    |
| ---------- | -------------------------- |
| `greet`    | the function object itself |
| `greet()`  | execute/call the function  |

This distinction becomes critically important later for:

* decorators
* callbacks
* event systems
* higher-order functions
* frameworks like Flask/Django/FastAPI

Most beginners never deeply internalize this distinction.

---

### 3. Why does `greet is x` return True?

`is` checks object identity, not equality.

Both names reference the exact same function object.

Equivalent idea:

```python
id(greet) == id(x)
```

---

### 4. What does this reveal about Python functions internally?

Functions are regular runtime objects.

This changes everything.

You can:

* store them in variables
* pass them into functions
* return them from functions
* place them in lists/dicts
* dynamically generate them
* wrap them
* modify behavior at runtime

Modern Python frameworks heavily depend on this.

Example:

```python
def shout():
    return "HEY"

def execute(func):
    print(func())

execute(shout)
```

Output:

```python
HEY
```

Why?

Because functions are objects that can move through the program like data.

Next, exercise will build that foundation.
