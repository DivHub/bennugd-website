---
modules:
- mod_mem
title: memory_free()
---

## Definition

    INT memory_free ( )

Returns the free memory total in bytes.

Also called `mem_available()`.

## Returns

- INT : Free memory total in bytes.

## Example

```
import "mod_mem"
import "mod_say"

Process Main()
Begin

    say("Total memory: " + memory_total());
    say("Free memory:  " + memory_free() );

End
```

Used in example: say(), memory_total(), memory_free()
