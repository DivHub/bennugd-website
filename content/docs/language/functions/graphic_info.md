---
modules:
- mod_map
title: graphic_info()
---

## Definition

    INT graphic_info ( <INT fileID> , <INT graphID> , <INT infotype> )

Gets some information about the graph specified.

This function is also known as `map_info()` and `map_info_get()`.

## Parameters

- INT fileID - The file that holds the graph.
- INT graphID - The graph to get information from.
- INT infotype - What type of information you want. Refer to [Graphical Infotypes]({{< ref "/docs/language/constants/graphical_infotypes" >}}).

## Returns

INT : Returns the information you want.

- If the specified graph was invalid it returns `0`.
- If the specified infotype was not recognized it returns `1`.

## Example

```
Program keuken;
Local
    gxc;
    gyc;

Begin

    set_mode(640,480,16);

    graph=new_map(rand(50,150),rand(50,150),16); //makes a randomly proportioned red rectangle
    map_clear(0,graph,rgb(255,0,0));
    x=320;
    y=240;

    gxc=graphic_info(0,graph,G_X_CENTER);
    gyc=graphic_info(0,graph,G_Y_CENTER);  //finds the graphic's center coordinates

    map_put_pixel(0,graph,gxc,gyc,rgb(255,255,255)); //puts a white pixel in the center of the graphic

    Loop

        frame;
    End
End
```

Used in example: [`set_mode()`]({{< ref "/docs/language/functions/set_mode" >}}), [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`map_put_pixel()`]({{< ref "/docs/language/functions/map_put_pixel" >}}).
