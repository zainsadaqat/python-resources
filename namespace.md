# Namespace in Python

A namespace is a container of names.

Think:

Each module has its own “box” of names.

`import math`

Now:

`sqrt lives inside math`

You must call:

`math.sqrt(4)`

Not:

`sqrt(4)` ❌

Because sqrt is not in your current namespace.

## from ... import ...

```py
from math import sqrt

print(sqrt(4))
```

Now:

sqrt is directly available in your namespace.

No prefix needed.

## Import Multiple Things

`from math import sqrt, pi`

## Import Everything (danger)

`from math import *`

This dumps everything into your namespace.

Problem:

- Name collisions
- Hard to debug
- No clarity

Never use this in serious code.

Aliasing

## Rename imports:

```py
import math as m

m.sqrt(4)
```

or

```py
from math import sqrt as s

s(4)
```

It's used for shortening names and avoiding conflicts

## Real Namespace Collision

```py
from math import sqrt

def sqrt(x):
    return "fake"

print(sqrt(4))
```

Result:

Your function overrides the imported one.

Namespace is overwritten.

## Module Search Path (important)

When you do:

```py
import mymodule
```

Python searches:

- Current directory
- Installed packages
- Standard library

If not found → error

## __name__ behavior

Inside a module:

```py
print(__name__)
```

If run directly → "__main__"

If imported → module name

Used for:

```py
if __name__ == "__main__":
```

It runs only if file executed directly
