---
modules:
- internals
title: "TRUE"
---

## Definition

    INT TRUE

`TRUE` is a constant integer, equal to the value 1. It is used to state that something is true and not false.

Checking whether a variable is true, is the same as checking if it's nonzero.

## Example

```
Program example;
Private
    int b = true;
Begin

    // comparison with the constant TRUE
    if(b == true)
        say("b was TRUE! so b==1");
    else
        say("b was not TRUE! so b!=1");
    end

    // checking the integer itself
    if(b)
        say("b was true! so b!=0");
    else
        say("b was false! so b==0");
    end

    Loop
        frame;
    End

End
```

## See also

 - [`FALSE`]({{< ref "/docs/language/constants/false" >}})
