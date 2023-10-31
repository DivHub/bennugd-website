---
modules:
- mod_mem
title: memory_total()
---

## Definition

    INT memory_total ( )

Returns the memory total in bytes.

Also called `mem_total()`.

## Returns

INT : Memory total in bytes.

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
