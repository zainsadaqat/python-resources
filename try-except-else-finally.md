# Try Except Else Finally

## try
This is where you place the "risky" code that might trigger an error (e.g., dividing by zero or opening a missing file).

## except
This block runs only if an error occurs in the try block. You can catch specific errors like ValueError or use a general except to catch anything.

## finally
This block runs regardless of whether an error happened or not. It is primarily used for cleanup tasks, such as closing files or database connections.

## else (Optional)
This block runs only if no exception was raised in the try block.

```py
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ZeroDivisionError:
    print("Error: You cannot divide by zero!")
except ValueError:
    print("Error: Please enter a valid integer.")
else:
    print(f"Success! The result is {result}")
finally:
    print("Cleanup: This runs no matter what.")
```

## Pro Tips

### Catch Specifics
It’s best practice to catch specific exceptions (like FileNotFoundError) rather than using a "bare" except:, which can hide bugs you didn't anticipate.

### The Return Rule
The finally block is so persistent it will even execute after a return statement in a function.
