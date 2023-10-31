---
title: const
---

    Const
        [ <constants> ]
    End

Const is a reserved word used to initiate the declaration of constants. Terminating the declaration block with an End is needed when the Const statement is not used in conjunction with the main code of the Program.

When declaring constants inside this construct, it's now allowed to explicitly name the type of the constant, i.e. you only have to assign the constant the value you want (see the example).

For a list of predefined constants, see this page.

## Example

```
Const
    // Declare constants here
    myInt = 4;
    myString = "hello";
End

Process Main()
Begin
End

Const
    // Declare constants here
End

```
