---
modules:
- mod_say
title: say_fast()
---

## Definition

    INT say_fast ( <STRING message> )

Prints message to stdout (console).

This function is the same as the [`say()`]({{< ref "/docs/language/functions/say" >}}) function, but with the difference that the debugging information isn't flushed (buffered) into the standard output.

As you can see in the bennu source code `mod_say.c`, the difference is only 1 instruction, so it's slightly faster.

- Similar to `System.out.println(message)` in Java.
- Similar to `printf("%s\n",message)` in C

## Parameters

- STRING message - The message to print on to the console

## Returns

INT - true

## Example

```
// import modules
IMPORT "mod_say";
IMPORT "mod_debug";


GLOBAL

int count;

PROCESS main();

BEGIN

   say("hello world.");
   say("");
   say("");
   FOR (count=0; count<5000; count+=1)
      say_fast("count: "+count);
   END
END
```

This will result in the output on console:

>Hello World!
