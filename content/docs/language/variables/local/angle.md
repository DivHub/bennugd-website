---
title: angle
---

## Definition

    INT angle = 0

Angle is a predefined [local variable]({{< ref "docs/language/variables/local/" >}}) which holds the angle (measured in 1/1000 of a degree) at which the graphic of that process (assigned by the local variable graph) will be drawn. It also influences the result of the function [`advance()`]({{< ref "advance" >}}).

An angle of 0 means to the right, 90000 means up, 180000 means left and 270000 and -90000 mean down.

## Example

To make the graphic of a process spin

```
import "mod_grproc"
import "mod_map"
import "mod_wm" // for exit_status
import "mod_key" // for key()

Process Main()
Begin
    graph = map_new(100,100,8);  //Create a cyan square and assign it to 'graph'
    map_clear(0,graph,rgb(0,255,255));
    x = 160;     //Position the graphic's center
    y = 100;     //in the center of the screen
    Repeat
        angle += 1000;    //increase the angle of graphic by 1000 each frame. 1000 = 1 degree.
        frame;
    Until(key(_ESC) || exit_status)
OnExit
    map_unload(0,graph);
End
```

Used in example: [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`rgb()`]({{< ref "/docs/language/functions/rgb" >}}), [`map_unload()`]({{< ref "/docs/language/functions/map_unload" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), exit_status, [`graph`]({{< ref "graph" >}}), x, y, angle

This process will spin the cyan square by 1 degree each frame.
