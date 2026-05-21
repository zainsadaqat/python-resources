# Scope in Python

In Python, scope defines the region of a program where a variable is accessible. 

Python resolves these rules using the LEGB rule, searching through four distinct layers in a specific order: 

Local, Enclosing, Global, and Built-in.

Here is the breakdown of all scopes and scenarios:1. The LEGB Resolution HierarchyWhen you reference a variable, Python searches for it in this exact order:L - Local: Names assigned within a function or method and not declared as global.E - Enclosing (or Nonlocal): Names in the local scope of any and all enclosing functions (e.g., in nested functions).G - Global: Names assigned at the top-level of a module file, or declared global within a function.B - Built-in: Names assigned in the built-in Python module (e.g., print, len, range).
