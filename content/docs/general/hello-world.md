---
title: Hello World
---

The Bennu **Hello World!** Example.

```
import "mod_say" // import the module to output text to console, using say()

Process Main() // start the definition of the main process
Begin // start the code
    say("Hello World!");
End // end the definition of the main process
```

This will import the module [`mod_say`]({{< ref "docs/language/modules/mod_say" >}}) which contains the definition of the [`say()`]({{< ref "/docs/language/functions/say" >}}) function. The function will echo the argument "Hello World" to the screen.
