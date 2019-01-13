+++
categories = ["functions", "math"]
layout = "function"
module = "mod_math"
title = "pow()"

+++

## Definition

    FLOAT pow ( <FLOAT base> , <FLOAT power> )

Returns *base* to the power of *power* (`base^power`).

## Parameters

- FLOAT base - The base.
- FLOAT power - The power.

## Returns

FLOAT : base to the power of power (base^power).

## Example

```
Program powerful;
Global
    float value1;
    int   value2;
Begin

    write_float(0,0, 0,0,&value1);
    write_int  (0,0,10,0,&value2);

    value1 = pow(2.3,4.6);
    value2 = pow(2  ,3  );

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: write_float(), write_int(), pow(), key().
