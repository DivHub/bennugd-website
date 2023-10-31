---
modules:
- mod_say
title: say()
---

## Definition

    INT say ( <STRING message> )

Prints message to stdout (console).

 - Similar to `System.out.println(message)` in Java.
 - Similar to `printf("%s\n",message)` in C

## Parameters

- STRING message - The message to print to stdout

## Returns

INT - true

## Example

```
import "mod_say"

Process Main()
Begin
    Say("Hello World!");
End
```

This will result in the output on console:

>Hello World!
