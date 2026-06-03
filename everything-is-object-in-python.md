# Everything is an Object in Python

In Python, "everything is an object" means that every single piece of data—including numbers, strings, functions, and even modules—is an instance of a corresponding class. 

They are all created equal in memory, meaning you can treat them all in the exact same way.

Here is exactly why we say this and what it means for your code:

## 1. Everything has an "Identity," a "Type," and a "Value"

Every object in Python possesses these three core traits:

Identity: A unique memory address (you can see it using id()).

Type: Defines what the object is and what it can do (checked using type()).

Value: The actual data it holds.

Even a simple number like 5 has a type (int) and a specific memory address, just like a complex object you create yourself.

## 2. You can pass anything to functions 

Because functions, strings, and integers are all objects, you can treat them all exactly the same. You can pass an integer, a list, or a function as an argument to another function.

### Example 

A function can take another function as input, modify it, or return it just as easily as passing the number 5.

### 3. Data and behaviors are bundled together

Every object can have its own data (attributes) and functions (methods). 

Even a basic string has built-in methods you can call using dot notation, like "hello".upper().

## 4. Even "things that do things" are objects

In many languages, functions and classes are special structures. 

### In Python

Functions are objects of the function class.

Classes themselves are objects of the type class.

Because they are objects, you can assign a function to a variable or store it inside a list.

Why this matters to you, This design gives Python incredible flexibility. 

It allows for powerful features like decorators (functions that modify other functions) and makes the language highly dynamic, 

since you can inspect or alter almost any part of your program while it is running.

### Example

```py
# A simple integer is an object
num = 42
print(type(num))  # Output: <class 'int'>
print(id(num))  # Output: (Unique memory address number)

# A function is also an object
def greet():
    return "Hello!"


print(type(greet))  # Output: <class 'function'>
print(
    id(greet)
)  # Output: (Another unique memory address)


# To make your own object, define a blueprint using a class.
class Dog:
    # The initializer sets up object data (attributes)
    def __init__(self, name):
        self.name = name

    # A behavior (method) the object can do
    def bark(self):
        return f"{self.name} says woof!"


# Create an instance (object) of the Dog class
my_dog = Dog("Buddy")

print(type(my_dog))  # Output: <class '__main__.Dog'>
print(my_dog.bark())  # Output: Buddy says woof!

```

