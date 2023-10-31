---
modules:
- internals
title: "FALSE"
---

## Definition

    INT FALSE

`FALSE` is a constant integer, equal to the value 0. It is used to state that something is false and not true.

Checking whether a variable is false, is the same as checking if it's zero.

## Example

```
Program example;
Private
    int b = false;
Begin

    // comparison with the constant FALSE
    if(b == false)
        say("b was FALSE! so b==0");
    else
        say("b was not FALSE! so b!=0");
    end

    // checking the integer itself
    if(!b)
        say("b was false! so b==0");
    else
        say("b was true! so b!=0");
    end

    Loop
        frame;
    End

End
```

## See also

 - [`TRUE`]({{< ref "/docs/language/constants/true" >}})
