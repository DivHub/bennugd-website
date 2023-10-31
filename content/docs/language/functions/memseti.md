---
modules:
- mod_mem
title: memseti()
---

## Definition

    INT memseti ( <VOID POINTER data> , <INT value> , <INT ints> )

Sets all ints in the specified memory block to the specified value.

Also called `mem_seti()`.

## Parameters

- VOID POINTER data   - Pointer to the block of ints in memory.
- INT value   - Value to set all ints to.
- INT ints    - Number of ints to change the value of.

## Returns

INT : true

## Example

See [`alloc()`]({{< ref "/docs/language/functions/alloc" >}}).

Also useful in conjunction with `map_buffer()` with 32 bits maps. (*Example Needed*).
