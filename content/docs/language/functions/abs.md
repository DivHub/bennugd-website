---
modules:
- mod_math
title: abs()
---

## Definition

    FLOAT abs ( <FLOAT value> )

Returns the absolute value of `value`.

## Parameters

- FLOAT value - The value.

## Returns

FLOAT : The absolute value of value.

## Example

```
Global
    float value1;
    int value2;
End

Process Main()
Begin

    write_float(0,0, 0,0,&value1);
    write_int(0,0,10,0,&value2);

    value1 = abs(3);
    value2 = abs(-4);

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: [`write_float()`]({{< ref "/docs/language/functions/write_float" >}}), [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}), abs(), [`key()`]({{< ref "/docs/language/functions/key" >}}).
