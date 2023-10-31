---
modules:
- mod_screen
title: put()
---

## Definition

    INT put ( <INT fileID> , <INT graphID> , <INT x> , <INT y> )

Draws (blits) a graph onto the background.

For more advanced blitting, see:

- [`xput()`]({{< ref "/docs/language/functions/xput" >}})
- [`map_put()`]({{< ref "/docs/language/functions/map_put" >}})
- [`map_xput()`]({{< ref "/docs/language/functions/map_xput" >}})
- [`map_xputnp()`]({{< ref "/docs/language/functions/map_xputnp" >}})

## Parameters

- INT fileID - The file that holds the graph.
- INT graphID - The graph to draw with.
- INT x - Where on the background's x-axis to put the graph.
- INT y - Where on the background's y-axis to put the graph.

## Returns

INT true

## Notes

The `x` and `y` parameters denote where to draw the graph, that is, where the center of the to be drawn graph will be.

## Errors

Unsupported color depth - The origin graph's color depth is greater than the destination graph's.

## Example

```
import "mod_map"
import "mod_screen"
import "mod_key"

Process Main()
Private
    int map;
Begin

    // Create a new graph of size 100x100 and color depth of 8bit
    map = map_new(100,100,8);

    // Clear the map red
    map_clear(0,map,rgb(255,0,0));

    // Put it in the center of the screen
    put(0,map,160,100);

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`put()`]({{< ref "/docs/language/functions/put" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}).
