---
modules:
- mod_blendop
title: blendop_new()
---

## Definition

    INT blendop_new ( )

Creates a new blend table. This table will contain a blending effect, which you'll have to set afterwards, using the various functions. When that is done you can finally apply or assign the blend table to a graphic.

The source section of the blend table will be the normal object and the destination section will be cleared, removing translucency.

## Parameters

## Returns

- 0 - Error: insufficient memory or the screen was not yet initialized.
- !0 - Success (pointer to the blend table).

## Notes

The right order of doing blending stuff: First create a new table with `blendop_new()`, then put a blending effect in it with for example `blendop_tint()`, and then assign it to a graphic with `blendop_assign()`.

Blendops are not supported in 32bit mode.

## Errors

Insufficient memory - There is insufficient memory available. This error doesn't occur often.

## Example

```
Program test;
Private
    int blendTable;
Begin

    set_mode(320,240,16);

    x = 160;
    y = 120;

    graph = new_map(100,100,16);
    map_clear(0,graph,RGB(255,255,255));

    blendTable = blendop_new();
    blendop_tint(blendTable,1,255,0,0);

    Repeat
        if (key(_space))
            blendop_assign(0,graph,blendTable);
        else
            blendop_assign(0,graph,NULL);
        end
        frame;
    Until(key(_ESC))

OnExit

    unload_map(0,graph);

End
```

Used in example: `set_mode()`, `new_map()`, `map_clear()`, `blendop_new()`, `blendop_tint()`, `key()`, `blendop_assign()`, `unload_map()`
