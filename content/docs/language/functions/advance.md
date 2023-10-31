---
modules:
- mod_grproc
title: advance()
---

## Definition

    INT advance ( <INT distance> )

Moves the calling process forward by distance units in the direction of the process' angle.

This function is influenced by the local variables angle and resolution.

## Parameters

- INT distance - Distance to advance, in units.

## Returns

INT : Returns true if successful and false if failed.

## Example

```
import "mod_grproc"
import "mod_map"
import "mod_wm" // for exit_status
import "mod_key" // for key()
import "mod_proc"

Process Main()
Private
    int my_proc;
Begin

    proc(); //create a new process
    proc2(); //create a new process

    Repeat
        frame;
    Until(key(_ESC) || exit_status)

OnExit

    signal(my_proc,S_KILL);

End

Process proc()
Begin

    // Create a cyan square and assign it to 'graph'
    graph = map_new(100,100,8);
    map_clear(0,graph,rgb(0,255,255));

    // Set starting position
    x = 50;
    y = 50;

    // This loop makes this process advance 3 pixels every frame
    Loop
        advance(3); // advance 3 pixels
        frame;
    End

End

Process proc2()
Begin

    // Set resolution to 100
    resolution = 100;

    // Create a cyan square and assign it to 'graph'
    graph = map_new(100,100,8);
    map_clear(0,graph,rgb(0,255,255));

    // Set starting position
    x = 50*resolution;
    y = 150*resolution;

    // This loop makes this process advance 3/100 pixels every frame
    Loop
        advance(3); // advance 3/100 pixels
        frame;
    End

OnExit

    map_unload(0,graph);

End
```

Used in example: [`key()`]({{< ref "/docs/language/functions/key" >}}), [`signal()`]({{< ref "/docs/language/functions/signal" >}}), [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`rgb()`]({{< ref "/docs/language/functions/rgb" >}}), [`advance()`]({{< ref "/docs/language/functions/advance" >}}), [`map_unload()`]({{< ref "/docs/language/functions/map_unload" >}}), exit_status, graph, x, y, resolution
