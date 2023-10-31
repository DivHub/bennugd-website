---
title: debug
---

    debug;

Debug is a reserved word used to tell Bennu to go into debug mode, only if the DCB was compiled with debug information (compiler option `-g`). If the module [`mod_debug`]({{< ref "mod_debug">}}) was imported as well, the console is immediately invoked and one can begin tracing from the debug statement.

Here's a handy page about debugging a Bennu program.

## Example

```
Function int debug_warning(string warning)
Begin
    say("Warning: " + warning);
    debug;
    return 0;
End
```

Used in example: say(), debug
