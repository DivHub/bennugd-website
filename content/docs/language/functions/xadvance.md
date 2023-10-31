---
modules:
- mod_grproc
title: xadvance()
---

## Definition

    INT xadvance ( <INT angle> , <INT distance> )

Moves a process a certain distance in a certain direction.

## Parameters

- INT angle - The angle in which to move the process, in thousandths of a degree.
- INT distance - The distance to move the process, in pixels.

## Returns

INT : Successrate

- `false` - Error.
- `true`  - Success.

## Example

```
Program example;
Global
    myproc;

Begin

    myproc=proc();

    Loop
        frame;
    End
End

Process proc();
Begin

    x=100;
    y=100;

    Loop
        xadvance(90000,10); //moves the process vertically (90 degrees) 10 pixels
        frame;
    End

End
```

