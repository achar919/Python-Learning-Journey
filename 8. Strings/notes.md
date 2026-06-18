# Complete String Methods Reference

Here is every string method covered in this part, in one place. Every method returns a new value — the original string is never modified.

| Method                | What It Does                                                        | Returns |
| --------------------- | ------------------------------------------------------------------- | ------- |
| `.upper()`            | All characters to uppercase                                         | `str`   |
| `.lower()`            | All characters to lowercase                                         | `str`   |
| `.title()`            | First letter of each word capitalized                               | `str`   |
| `.capitalize()`       | Only the first character capitalized                                | `str`   |
| `.strip()`            | Removes whitespace from both sides                                  | `str`   |
| `.lstrip()`           | Removes whitespace from left side                                   | `str`   |
| `.rstrip()`           | Removes whitespace from right side                                  | `str`   |
| `.split(sep)`         | Splits string into a list by separator (default: whitespace)        | `list`  |
| `sep.join(list)`      | Joins list items into a string with separator                       | `str`   |
| `.replace(old, new)`  | Replaces all occurrences of old with new                            | `str`   |
| `.find(sub)`          | Returns index of first occurrence, or `-1` if not found             | `int`   |
| `.index(sub)`         | Returns index of first occurrence, raises `ValueError` if not found | `int`   |
| `.startswith(prefix)` | Checks if string starts with prefix                                 | `bool`  |
| `.endswith(suffix)`   | Checks if string ends with suffix                                   | `bool`  |
| `.count(sub)`         | Counts non-overlapping occurrences of substring                     | `int`   |
| `.isdigit()`          | `True` if all characters are digits                                 | `bool`  |
| `.isalpha()`          | `True` if all characters are letters                                | `bool`  |
| `.isalnum()`          | `True` if all characters are letters or digits                      | `bool`  |
| `.isupper()`          | `True` if all cased characters are uppercase                        | `bool`  |
| `.islower()`          | `True` if all cased characters are lowercase                        | `bool`  |
| `.zfill(width)`       | Pads with zeros on the left to fill width                           | `str`   |
| `.center(width)`      | Centers string within width, padding with spaces                    | `str`   |
| `.ljust(width)`       | Left-justifies string within width                                  | `str`   |
| `.rjust(width)`       | Right-justifies string within width                                 | `str`   |

# Method Chaining

Because every string method returns a new string, you can chain them:

```python
raw = "   Hello, WORLD!   "
clean = raw.strip().lower().replace("!", "")
print(clean)   # "hello, world"
```

Each method operates on the result of the previous one. This is a common and clean pattern in Python.

# Unicode Awareness

Python strings support Unicode — they can hold characters from any language:

```python
greeting = "ನಮಸ್ಕಾರ"  # Kannada
print(greeting)
print(len(greeting))
```

Python handles multi-language text natively. This is important for applications that serve users in different languages.
