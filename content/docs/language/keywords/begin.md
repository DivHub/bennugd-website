---
title: begin
---

    Begin
    [ <main code> ]
    [ OnExit
        [ <exit code>]
    ] End

Begin is a reserved word to indicate the start of the code part of a program, process or function. The end is indicated by End. The OnExit statement can be used in between.

## Example

```
Process Main
Begin // Start the main code part of the main process
    proc1(); // create new instance of proc1
End

Process proc1()
Begin // Start the main code part of the process
End

Function int func1()
Begin // Start the main code part of the function
    return 0;
End
```
