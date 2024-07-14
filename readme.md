# Simple Configuration Language

SCL aims to be a text-based data format that is easy to read and not difficult to parse.
Language rules are a merge of json, yaml and toml. It is suitable for human-readable
config files with comments, formatting and indentation as well as slightly less noisy
json alternative.

Syntax is not dependant on newlines, formatting and indentation, although users are encouraged
to use them for readability. Property names must use only alphanumerical words. Properties
have optional type hints.

## Example

```scl
# line comment

filename = "readme.md" # property with string value

/*
block comment

properties can be either:
    1. integer number (includes negative values)
    2. float number
    3. boolean (true/false)
    4. string ("foo string")
    5. object
    6. list
    7. eval block ($()) (TODO: more clear rules and examples)
    8. skip syntax (... means that default value should be used)
    9. not present (somewhat meta-option)

integers can be in different formats:
    - decimal (54)
    - hexadecimal (0xf3)
    - octal (0o451)
    - binary (0b1011)
*/

enable_logs = true
max_lines   = 24

min_ratio = 2.05

# list of strings
files = [
    "main.c"
    "lib.h"
    "lib.c"
]

logs = {
    enable = true
    level  = "info"
    file   = ... # use default file
}

list_of_objects = [
    {
        foo = "bar"
        bar = "foo"
    }
    {
        foo = "foo"
        bar = "bar"
        count = 3
    }
]

extensions_dir = $(filename)

with_type_hint (string) = "name"
```
