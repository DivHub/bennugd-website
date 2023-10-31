---
modules:
- mod_string
title: trim()
---

## Definition

    STRING trim ( <STRING str> )

Returns a copy of str without leading or ending whitespace (spaces, tabs, linefeeds, carriage returns).

## Parameters

- STRING str  - The string to trim.

## Returns

STRING: trimmed string

## Example

```
import "mod_string"
import "mod_say"

Const
    _ABC_ = " ABC ";
End

Process Main()
Private
    string ABC;
Begin

    ABC = trim(_ABC_);
    say('_ABC_ = "' + _ABC_ + '"');
    say('ABC = "' + ABC + '"');

End
```

Result:
```
_ABC_ = " ABC "
ABC = "ABC"
```

Used in example: say(), trim()
