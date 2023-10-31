---
title: Local Variables
weight: 5
---

A local variable is a variable that is specific to a process in the same way as a public variable: they are both accessible from other places in the code than the process/function itself. However, unlike a public variable, when a local variable is declared, all following processes will have that local.

There's also a number of predefined [global variables]({{< ref "docs/language/variables/global/" >}}).

To start the declaration of local variables, use [`Local`]({{< ref "docs/language/keywords/local" >}}).

## Example

```
Local
    // insert local variables that you can use here
End

Process Main()
Begin
    // main code
End
```
