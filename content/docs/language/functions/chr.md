---
modules:
- mod_string
title: chr()
---

## Definition

    STRING chr ( <BYTE ASCIIvalue> )

Returns the character associated with ASCIIvalue.

## Parameters

- BYTE ASCIIvalue - The ASCII value of which the character is wanted.

## Returns

STRING : The character associated with ASCIIvalue.

## Example

```
Program chars;
Begin

    write(0,0, 0,0,chr(65));
    write(0,0,10,0,chr(67));

    Repeat
        frame;
    Until(key(_esc))

End
```

Used in example: write(), key()
