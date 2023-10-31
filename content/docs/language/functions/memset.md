---
modules:
- mod_mem
title: memset()
---

## Definition

    INT memset ( <VOID POINTER data> , <BYTE value> , <INT bytes> )

Sets all bytes in the specified memory block to the specified value.

Also called `mem_set()`.

## Parameters

- VOID POINTER data - Pointer to the block of bytes in memory
- BYTE value - Value to set all bytes to.
- INT bytes - Number of bytes to change the value of.

## Returns

INT : true

## Example

See [`alloc()`]({{< ref "/docs/language/functions/alloc" >}}).

Also useful in conjunction with `map_buffer()` with 8bit maps. (Example can be found in the `map_buffer` article.)
