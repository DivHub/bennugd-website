---
modules:
- mod_grproc
title: get_angle()
---

## Definition

    INT get_angle ( <INT processID> )

Returns the angle between the coordinates of a certain process and the process calling `get_angle()`.

## Parameters

- INT processID - The other process.

## Returns

INT : The wanted angle.

- `-1` - An error may have occurred: invalid process.
- `!-1` - The wanted angle.

## Example

```
Program angling;
import "mod_grproc"//modules
import "mod_proc"
import "mod_wm"
import "mod_key"
import "mod_video"
import "mod_map"
import "mod_draw"
import "mod_text"
Const
    screen_width     = 320;
    screen_height    = 200;
    screen_depth     = 8;
    screen_fps       = 60;
    screen_frameskip = 0;
Global
    int distance;
    int tempID;
Begin

    // Set the screen mode
    set_mode(screen_width,screen_height,screen_depth);
    set_fps(screen_fps,screen_frameskip);

    // Change this to see what happens
    resolution = 100;

    // Create mouse graph and start mousepointer
    x = map_new(20,20,screen_depth);
    map_clear(0,x,rgb(255,0,0));
    mousepointer(0,x);

    // Create arrow, assign to graph
    graph = map_new(30,30,screen_depth);
    drawing_map(0,graph);
    drawing_color(rgb(0,255,0));
    draw_line( 0,29,29,30/2);
    draw_line( 0, 0,30,30/2);

    // Set position
    x = screen_width /2 * resolution;
    y = screen_height/2 * resolution;

    // Display distance
    write(0,0,0,0,"Distance:");
    write_int(0,60,0,0,&distance);

    // Always point to the mouse
    Repeat
        // Get the angle and distance between this process' coordinates and those of mousegraph.
        // We can use TYPE and get_id() here, because usually there would only be one
        // mousepointer and one always.
        tempID = get_id(type mousepointer);
        angle = get_angle(tempID);
        distance = get_dist(tempID);
        frame;
    Until(key(_esc))

End

/**
 * Follows the mouse coordinates. x is always mouse.x and y is always mouse.y
 * for processes with priority <1. The graphic of this process will be a certain graphic.
 * int file     - The fileID of the file where the graphic is located
 * int graph    - The graphID of the graphic to be used for this process
 */
Process mousepointer(int file,int graph)
Begin
    // Set the priority to 1, because we first want to have the correct coordinates of
    // the mouse set in this process. Then after that other process can use those coordinates.
    priority = 1;
    // Obtain father's resolution
    resolution = father.resolution;
    // Loop
    Loop
      // Obtain X and Y coordinates of the mouse and adjust for resolution
        // (mouse.y and mouse.y have an unchangeable resolution of 1)
        x = mouse.x * resolution;
        y = mouse.y * resolution;
        frame;
    End
End
```

Used in example: [`set_mode()`]({{< ref "/docs/language/functions/set_mode" >}}), [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`drawing_map()`]({{< ref "/docs/language/functions/drawing_map" >}}), [`drawing_color()`]({{< ref "/docs/language/functions/drawing_color" >}}), [`draw_line()`]({{< ref "/docs/language/functions/draw_line" >}}), [`write()`]({{< ref "/docs/language/functions/write" >}}), [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}), [`get_id()`]({{< ref "/docs/language/functions/get_id" >}}), [`get_angle()`]({{< ref "/docs/language/functions/get_angle" >}}), [`get_dist()`]({{< ref "/docs/language/functions/get_dist" >}}),resolution, mouse, graph, x, y, angle, priority

This example could also be done with [`fget_angle()`]({{< ref "/docs/language/functions/fget_angle" >}}), which is easier and doesn't require an extra process.

> It could look something like: http://wwwhome.cs.utwente.nl/~bergfi/fenix/wiki/get_angle.PNG

