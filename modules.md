# Modules in Python

A module is just a Python file.

If you create: `math_utils.py`

That file is a module.

Anything inside it (variables, functions) can be reused.

For Example: 

**_math_utils.py_**

```py
def add(a, b):
    return a + b
```

## Importing a Module

```py
import math_utils

result = math_utils.add(2, 3)
```

Key rule:

You must use the module name as a prefix.

This prevents naming conflicts.
