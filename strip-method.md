The strip() method removes any leading, and trailing whitespaces.

Leading means at the beginning of the string, trailing means at the end.

You can specify which character(s) to remove, if not, any whitespaces will be removed.

## Example

```py
txt = ",,,,,rrttgg.....banana....rrr"

x = txt.strip(",.grt")

print(x)
```
