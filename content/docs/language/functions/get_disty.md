---
modules:
- mod_math
title: get_disty()
---

## Definition

    INT get_disty ( <INT angle> , <INT distance> )

Returns the vertical distance in pixels of a specified displacement.

This is the same as `-sin(angle) * distance`.

## Parameters

- INT angle - Angle, in thousandths of degrees (90° = 90000).
- INT distance - Length (in pixels) to measure.

## Returns

INT : The vertical distance, in pixels, of a specified displacement.

## Notes

This function returns the height of an imaginary rectangle who's opposite corners are the specified distance apart, at the specified angle from each other.

## Example

```
Global
    xdist;
    ydist;
    dist;
    ang;
    mydraw;
End

Process Main()
Begin

    set_mode(640,480,16);
    set_fps (50,0);
    graph = new_map(3,3,16);
    map_clear(0,graph,rgb(0,255,0));
    x = 320;
    y = 240;

    set_text_color(rgb(0,0,0));
    write    (0,60, 0,2,"X Diff: ");
    write_int(0,60, 0,0,&xdist);
    write    (0,60,10,2,"Y Diff: ");
    write_int(0,60,10,0,&ydist);
    write    (0,60,20,2,"Angle: ");
    write_int(0,60,20,0,&ang);
    write    (0,60,30,2,"Distance: ");
    write_int(0,60,30,0,&dist);

    write    (0,10,40,0,"Left/right rotates your angle, up/down changes your distance");

    put(0,graph,x,y);
    drawing_background();

    repeat
        if(key(_up))
            dist++;
        end

        if(key(_down))
            dist--;
        end

        if(key(_left))
            ang-=1000;
        end

        if(key(_right))
            ang+=1000;
        end

        xdist = get_distx(ang,dist);
        ydist = get_disty(ang,dist);

        x = 320 + xdist;
        y = 240 + ydist;

        frame;

    until(key(_esc))

    let_me_alone();
    exit();

End

Process drawing_background()
Begin
    graph = new_map(640,480,16);
    set_ceter   (0,graph,0,0);
    map_clear    (0,graph,rgb(64,0,0));
    drawing_map  (0,graph);
    drawing_color(rgb(0,0,0));
    loop
        map_clear(0,graph,rgb(255,255,255));
        mydraw = draw_line(320,240,father.x,father.y);
        frame;
        delete_draw(mydraw);
    end
OnExit
    unload_map(0,graph);
End
```

Used in example: set_mode(), set_fps(), new_map(), set_text_color(), write(), write_int(), put(), key(), get_distx(), get_disty(), let_me_alone(), exit(), set_center(), map_clear(), rgb(), drawing_map(), drawing_color(), draw_line(), delete_draw(), unload_map()
