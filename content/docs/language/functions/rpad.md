---
modules:
- mod_string
title: rpad()
---

## Definition

    STRING rpad( <STRING str> , <INT length> )

Returns the string `str`, padding (adding spaces to) the back of the string if needed to make `str` of length `length`. The original string will remain unchanged.

If `length` is smaller or equal to the length of `str`, the returned string is `str`.

## Parameters

- STRING str  - The string to pad (add spaces to).
- INT length  - The minimal length of the returned string.

## Returns

STRING: padded string

## Example

```
import "mod_string"
import "mod_say"

Process Main()
Private
    string ABC = "ABC";
    string _ABC;
    string ABC__;
Begin

    ABC = lpad(ABC,2);
    _ABC = lpad(ABC,4);
    ABC__ = rpad(ABC,5);

    say('ABC = "' + ABC + '"');
    say('_ABC = "' + _ABC + '"');
    say('ABC__ = "' + ABC__ + '"');

End
```

Result:

```
ABC = "ABC"
_ABC = " ABC"
ABC__ = "ABC  "
```

Used in example: say(), lpad(), rpad()
