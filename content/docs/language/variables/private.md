---
title: Private Variables
---

A private variable is a variable that is specific to a process or function. Unlike a public variable, it can only be accessed from the process or function it was declared for.

To start the declaration of private variables, use [`Private`]({{< ref "docs/language/keywords/private" >}}).

## Example

```
Function int SomeFunction()
Private
    int i,j; // declare private ints i and j
    String strtemp; // declare private string strtemp
Begin
    // ...
    return 0;
End
```

Used in example: Function, Private, Begin, End

The private variables i and j could be variables used for counting and the string probably would have some use as well.
