# Dictionary in Python

## The big picture

A dictionary is fundamentally a combination of three ideas:

```
Key
        │
        ▼
Hash Function
        │
        ▼
Hash Value (integer)
        │
        ▼
Table Index
        │
        ▼
Hash Table (array)
        │
        ▼
Stored Key–Value Pair
```

## What is a hash?

A hash is just a number.

Nothing magical.

### Example

```
"Ali"
↓
837492

"John"
↓
182933

"Sarah"
↓
928372
```

Python converts objects into integers.

Those integers are called hash values.

Who creates that number?

A function.

Hash Function

Input

Sarah

Output

928372

Every time.

hash("Sarah")

↓

928372

The same input always produces the same hash value (during a given Python process for strings and some other types, Python intentionally randomizes hashes between different runs for security).

Notice

The function does not return the GPA.

It does not return the object.

It only produces a number.

## What is a hash table?

A hash table is simply a large array.

Imagine

```
Index

0

1

2

3

4

5

6

7

...

999
```

Initially

```
0 → empty

1 → empty

2 → empty

3 → empty
```

Now

```
student["Sarah"] = 3.9

Python does roughly

hash("Sarah")

↓

928372

Now it converts that hash into a valid table index.

Conceptually

928372

↓

372

Then stores

372

↓

("Sarah",3.9)
```

Notice

It didn't search.

It computed.

## The Pattern

Almost every dictionary problem is one of these:

Pattern	Example
Counting	Count words, votes, products, letters
Lookup	Student ID → Student
Remembering the past	Two Sum
Grouping	Employees by department
Caching	Save expensive computations
Fast existence check	Has this username already been used?

### 1. Why do dictionaries exist?
### 2. What problem do they solve?
### 3. How are they implemented conceptually (hash table, at a high level)?
### 4. When should you choose a dictionary instead of a list or tuple?
### 5. Time complexity of common operations.
### 6. Five real-world use cases (student records, inventory lookup, caching, API responses, frequency counting).
### Three interview questions that naturally require dictionaries.

A discussion of alternative solutions and their trade-offs.

By the end of the lesson, she should be able to justify why she chose a dictionary, not merely demonstrate that she knows how to write {}. That aligns exactly with the interview skills she wants to build.

## Lesson Goal

Before touching any code:

By the end of today's lesson, you won't just know how to use dictionaries. You'll know why they were invented, what problems they solve, when they're the best choice, when they're not, and how interviewers expect you to think about them.

### Step 1: Begin with a problem, not syntax

Never start with this:

```py
student = {
    "name": "John",
    "age": 20
}
```

Instead ask:

Imagine you work at a university.

There are 50,000 students.

The dean asks:

Find Sarah's GPA.

How would you store students?

Most beginners answer:
```
students = [
    ("Ali", 3.7),
    ("Sarah", 3.9),
    ("John", 3.2),
    ...
]
```
Ask:

How would you find Sarah?

They'll say:

for student in students:

Ask again.

What if there are 50,000 students?

Now they realize they'll have to check one student after another.

That's slow.

### Step 2: Why is this slow?

Draw it.

```
Ali
↓

Sarah
↓

John
↓

Mike
↓

Emma
↓

...
```

To find Emma

Python checks
```

Ali ❌

Sarah ❌

John ❌

Mike ❌

Emma ✅
```

Every search starts from the beginning.

#### Explain:

This is called linear search.

Time complexity

O(n)

If there are

10 students

maximum 10 comparisons

100 students

maximum 100 comparisons

1 million students

maximum 1 million comparisons

Ask:

Can we do better?

### Step 3: Invent the dictionary together

Suppose every student has a locker.

```
Ali

Locker 13

Sarah

Locker 87

John

Locker 42
```

Instead of searching every locker...

You already know Sarah belongs to locker 87.

You go directly.

That's the idea behind dictionaries.

Not searching.

Jumping.

Now introduce syntax.
```

students = {
    "Ali": 3.7,
    "Sarah": 3.9,
    "John": 3.2
}
```

Finding Sarah

```
students["Sarah"]
```

No loop.

No searching.

### Step 4: Why does this work?

This is where most tutorials stop.

You continue.

Ask

How does Python know where Sarah is?

Magic?

No.

Hashing

### Step 5: Explain hashing like a human

Imagine a huge apartment building.

1000 apartments.
```

1

2

3

...

1000
```

Every resident has a name.

Instead of asking every apartment

"Does Sarah live here?"

there is a machine.

Put in

Sarah

The machine says

Apartment 483

Immediately.

The machine always gives the same apartment.

Sarah

483

Sarah

483

Sarah

483

This machine is called a

Hash Function.

### Step 6: Hash Table

Draw this.
```
Index

0

1

2

3

4

5

6

...

483
↓

Sarah → 3.9

...

721
↓

Ali → 3.7
```

Python stores values in locations determined by hashing.

Instead of searching...

Python jumps directly.

### Step 7: Is it really O(1)?

Can Python always jump directly?

Mostly yes.

Sometimes two names produce the same index.

Example
```

Ali

→ 42

John

→ 42
```

Now Python has two people in one location.

This is called

Collision.

Python handles collisions internally.

So dictionary lookup is

Average

O(1)

Worst

O(n)

Average is what interviewers usually expect.

### Step 8: Why not use a list?

Suppose you only have numbers.

ages = [20, 21, 22]

Do you need names?

No.

Dictionary?

No.

List is simpler.

Suppose

student_names = [
    "Ali",
    "John",
    "Sarah"
]

Need Sarah.

Loop.

Dictionary better.

### Step 9: List vs Dictionary

#### List	

Ordered collection	
Access by index	
Search is O(n)	
Duplicate values 
Best for sequences	

#### Dictionary

Key-value mapping
Access by key
Lookup is O(1) average
Keys must be unique
Best for lookups

### Step 10: Tuple vs Dictionary

#### Tuple

("Ali",20)

Good when data never changes.

#### Dictionary

{
"name":"Ali",
"age":20
}

Readable.

Flexible.

Mutable.

### Step 11: Real-world 

#### Example-1

Student database

```
student = {
    "name":"Ali",
    "gpa":3.8,
    "major":"CS"
}
```

Instead of

student[0]

student[1]

student[2]

Much clearer.

#### Example-2

Inventory

```
inventory = {
    "Apple":120,
    "Banana":90,
    "Orange":15
}
```

Customer buys

Apple

Immediately

inventory["Apple"] -= 1

#### Example-3

API Response

Every REST API

{
"id":15,
"name":"John",
"email":"..."
}

JSON becomes Python dictionary.

#### Example-4

Caching

Instead of computing

factorial(500)

again

Store

cache = {
500: huge_answer
}

Next time

Return instantly.

#### Example-5

Frequency Counter

Apple

Banana

Apple

Apple

Orange

Produce

```
{
Apple:3,
Banana:1,
Orange:1
}
```

Very common interview problem.

### Step 12: Interview Questions

#### Question 1: Find first repeated character.

programming

Dictionary stores already seen letters.

#### Question 2: Most common word.

Dictionary counts frequencies.

#### Question 3: Two Sum.

nums

target

Dictionary remembers previously seen numbers.

Classic FAANG interview.

### Step 13: Alternatives

Suppose

Need unique values.

apple

banana

apple

orange

Dictionary?

No.

Set.

Need ordered sequence.

List.

Need fixed pair.

Tuple.

Need fast lookup.

Dictionary.

### Step 14: Trade-offs

Every data structure has a cost.

#### Dictionary advantages

- Extremely fast lookup
- Clear key-value relationships
- Excellent for mappings
- Easy to update

#### Dictionary disadvantages

- Uses more memory than a list
- Keys must be hashable (e.g., immutable types like strings, numbers, tuples)
- Not ideal when data is naturally sequential
- Average-case performance depends on a good hash distribution

### Step 15: Challenge

#### Scenario 1

Spotify stores millions of songs.

Should songs be stored in

List
Dictionary
Tuple

Why?

#### Scenario 2

Hospital

Find patient by ID.

Which data structure?

#### Scenario 3

Netflix

Count how many times every movie was watched.

Which data structure?

#### Scenario 4

Bank

Store transaction history in order.

Which one?

#### Scenario 5

Chess

Represent board coordinates like "e4" → piece.

Which one?

Final takeaway

By the end of the lesson, she should stop thinking:

"A dictionary is a Python data structure."

and start thinking:

"A dictionary is the right tool whenever I need to associate unique keys with values and perform fast lookups, updates, or membership checks. I choose it because its average-case operations are O(1), and I understand the trade-offs compared with lists, tuples, and sets."

That shift—from memorizing syntax to reasoning about data structures—is what technical interviews are designed to evaluate.
