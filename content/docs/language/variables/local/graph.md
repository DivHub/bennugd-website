---
title: graph
---

## Definition

    INT graph = 0

`graph` is a predefined local variable which holds the `GraphID` of the process. A graphic can be assigned to the process by assigning the `GraphID` of that graphic to `graph`.

Assign `0` to the local variable graph to have the process display no graph. Keep in mind that this doesn't free the memory used by the graphic; to free it, use [`map_unload()`]({{< ref "/docs/language/functions/map_unload" >}}).

## Example

```
Process cyan_graphic()
Begin
    graph = map_new(100,100,8);   // create a new 100x100x8 map.
    map_clear(0,graph,rgb(0,255,255));   // clear it cyan-colored
    x = 100;     //Position the graphic 100 pixels
    y = 100;     //from the top and left of the screen
    Repeat
        frame;
    Until(key(_ESC))
End
```

Used in example: [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), graph, x, y
