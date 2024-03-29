---
title: Blend Operations
---

A blend operation is the act of executing the blending of a graphic (source) with the pixels the graphic is drawn on (target) using a blend table.

This is done in two ways:

- The blendop is performed explicitly using [`blendop_apply()`]({{< ref "blendop_apply" >}}), modifying the graphic.
- The blendop is assigned to a graphic and performed implicitly when that graphic is drawn. This method is not available for modes lower than 16bit.

Blendops are not supported in 32bit mode.

Retrieved from "https://wiki.bennugd.org/index.php?title=Blend_operation&oldid=7411"

## Blend Table

A blend table contains the blend data needed to perform the blend between the object (source) and where the object is drawn (destination). The table contains those two sections: source and destination; these section are added together when blending (the adding function cannot be altered) and the sections can be influenced by the blend operations available.

One can even make homemade blending operations, if one has enough knowledge of the subject, as [`blendop_new()`]({{< ref "blendop_new" >}}) returns a pointer to the created blend table. This table is constructed like this:

| bytes-start | bytes-end | total | purpose |
|---|---|---|---|
| 0 | 65535 | 65536 | Source section |
|65536  | 131071 | 65536 | Destination section |
{ .table }

Each pixel of a section represents a colour. When a blend table is initialized, it's done like this:

```
for (i = 0 ; i < 65536 ; i++) source[i] = i ;
for (i = 0 ; i < 65536 ; i++) destination[i] = 0 ;
```

So:

- For the source section the following applies: The nth index has value n.
- For the destination section the following applies: The nth index has value 0.

Blendops are not supported in 32bit mode.

## Example

```
import "mod_screen"
import "mod_mouse"
import "mod_key"
import "mod_map"
import "mod_video"
import "mod_blendop"
import "mod_proc"
import "mod_draw"
import "mod_text"

Global
    int bo_tintred;
    int bo_tintredAndTranslucent;
    int bo_intense;
    int bo_destintense;
    int bo_grayscale;
    int bo_destgrayscale;
    int map;
End

Process Main()
Begin

    // Set mode to 320x200x16
    set_mode(320,200,16);

    // Init tables
    bo_tintred = blendop_new();
    bo_tintredAndTranslucent = blendop_new();
    bo_intense = blendop_new();
    bo_grayscale = blendop_new();
    bo_destintense = blendop_new();
    bo_destgrayscale = blendop_new();

    // Red tint
    blendop_tint(bo_tintred,0.5,100,0,0);

    // Red tint with translucency
    blendop_tint(bo_tintredAndTranslucent,0.5,250,0,0);
    blendop_translucency(bo_tintredAndTranslucent,0.5);

    // Intense
    blendop_intensity(bo_intense,1.5);

    // Display the destination intense
    blendop_intensity(bo_destintense,1.5);
    blendop_swap(bo_destintense);

    // Grayscale
    blendop_grayscale(bo_grayscale,1);

    // Display the destination in grayscale
    blendop_grayscale(bo_destgrayscale,3);
    blendop_swap(bo_destgrayscale);

    // Make a new map
    map = some_map(80,80,16);

    // Make the background rgb(50,150,150)
    map_clear(0,background,rgb(50,150,150));

    // Show the four different blend operations
    a( 50, 50,map,0,"original");
    a(150, 50,map,bo_tintred,"red");
    a(250, 50,map,bo_tintredAndTranslucent,"red+transparent");
    a( 50,150,map,bo_intense,"intense");
    a(150,150,map,bo_destintense,"dest instense");
    a(250,150,map,bo_grayscale,"grayscale");

    // Give this process one too
    blendop_assign(0,map,bo_destgrayscale);
    graph = map;

    Repeat
        x = mouse.x;
        y = mouse.y;
        if(mouse.left)
            z = -1;
        else
            z = 1;
        end
        frame;
    Until(key(_ESC))

OnExit
    let_me_alone();
End

/**
 * Description
 *   Create a new process at the given coordinates.
 *   Its graph will be cloned from the specified one and the
 *   specified blendtable will be assigned.
 *   The specified text will be put on the background below the graph.
 *
 * Parameters
 *   int x,y         - Coordinates the process will be at.
 *   int graph       - The graph to be cloned (file=0).
 *   int blendtable  - The blendtable to assign to the graph.
 *   int string text - The text to put on the map.
 *
 * Returns
 *   ProcessID
 */
Process a(int x,int y,int graph, int blendtable, string text)
Private
    int m;
Begin

    // Clone the map
    graph = map_clone(0,graph);

    // Assign the blend table
    blendop_assign(0,graph,blendtable);

    // Set z=0
    z = 0;

    // Create text and put it on the background
    set_text_color(rgb(100,200,250));
    m=write_in_map(0,text,1);
    put(0,m,x,y+1+graphic_info(0,graph,G_HEIGHT)/2);
    unload_map(0,m);

    // Loop
    Loop frame; End

End

/**
 * Description
 *   Creates a map with the four corners coloured differently.
 *
 * Parameters
 *   int x,y,z       - The width, height and depth of the map to be created.
 *
 * Returns
 *   The graphID of the created map
 */
Function int some_map(int x, int y, int z)
Begin
    z = new_map(x,y,z);
    map_clear(0,z,rgb(50,100,150));
    drawing_map(0,z);
    drawing_color(rgb(200,50,100));
    draw_box(0,0,x/2,y/2);
    drawing_color(rgb(0,250,100));
    draw_box(x/2,0,x,y/2);
    drawing_color(rgb(150,50,250));
    draw_box(x/2,y/2,x,y);
    return z;
End
```

Used in example: set_mode(), blendop_new(), blendop_tint(), blendop_translucency(), blendop_intensity(), blendop_swap(), blendop_grayscale(), map_clear(), blendop_assign(), key(), let_me_alone(), map_clone(), set_text_color(), write_in_map(), put(), unload_map(), new_map(), drawing_map(), drawing_color(), draw_box(), mouse

