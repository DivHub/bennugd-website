---
title: private
---

    Private
        [ <private variables> ]
    [End]

`Private` is a reserved word used to initiate the declaration of [private variables]({{< ref "/docs/language/variables/private" >}}). Terminating the declaration block with an [`End`]({{< ref "/docs/language/keywords/end" >}}) is not necessary, but is possible.

Parameters of a function or process will be considered a private variable with the initiated value of the passed argument.

## Example

```
Process My_Process();
Public
Private // Declare private variables here
Begin
End
```
