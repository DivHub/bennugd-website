---
modules:
- mod_string
title: strcasecmp()
---

## Definition

    INT strcasecmp( <STRING str1> , <STRING str2> )

Compares two strings case-insensitive and returns the result.

## Parameters

- STRING str1 - The first string.
- STRING str2 - The second string, to compare with the first string.

## Returns

INT: difference

- `0` - The strings are equal.
- `>0`  - The ASCII value of the first differing characters is higher for str1.
- `<0`  - The ASCII value of the first differing characters is higher for str2.

## Notes

If the strings differ, the ASCII difference between the first differing characters of the strings is actually returned. Let `i` be the index of the differing characters, then what is returned: `str1[i]-str2[i]`.

## Example

```
import "mod_string"
import "mod_say"

Const
    AB = "AB";
    ABC = "ABC";
    CD = "CD";
    CD2 = "CD";
End

Process Main()
Begin

    say("strcasecmp(AB,ABC) = " + strcasecmp(AB,ABC));
    say("strcasecmp(AB,CD) = " + strcasecmp(AB,CD));
    say("strcasecmp(CD,AB) = " + strcasecmp(CD,AB));
    say("strcasecmp(CD,CD2) = " + strcasecmp(CD,CD2));

End
```

Result:

```
strcasecmp(AB,ABC) = -67
strcasecmp(AB,CD) = -2
strcasecmp(CD,AB) = 2
strcasecmp(CD,CD2) = 0
```

Used in example: say(), strcasecmp()
