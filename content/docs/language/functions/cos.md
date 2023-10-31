---
modules:
- mod_math
title: cos()
---

## Definition

    FLOAT cos ( <FLOAT angle> )

Returns the cosine of the specified angle.

This function performs a cosine calculation on a certain [angle]({{< ref "angle" >}}) and returns a value between -1 and 1.

## Parameters

- FLOAT angle - [Angle]({{< ref "angle" >}}), in thousandths of degrees. i.e. 75000 = 75º

## Returns

FLOAT : The cosine result of the specified [angle]({{< ref "angle" >}}).

## Notes

The angle value used in this function should be in thousandths of degrees, as most angles within Bennu are.

To read about all aspects of trigonometry, you can visit Wikipedia's [Trigonometric functions](https://en.wikipedia.org/wiki/Trigonometric_functions) and [atan2](https://en.wikipedia.org/wiki/Atan2) pages.

## Example

```
Const
    screen_width  = 320;
    screen_height = 200;
    screen_border = 15;
End

Global
    float value;
End

Process Main()
Begin

    // Modes
    set_title("Cosine Graph");
    set_mode(screen_width,screen_height);

    // X axis
    for(x=1;x<=8;x++)
        write( 0,
               screen_border+x*(screen_width-screen_border)/8+3,
               screen_height-1,
               8,
               itoa(x*360/8 )+"^" );
    end
    draw_line(1,screen_height-screen_border,screen_width,screen_height-screen_border);

    // Y axis
    write(0,screen_border-1,20,5,"1");
    write(0,screen_border-1,screen_height/2,5,"0");
    write(0,screen_border-1,screen_height-20,5,"-1");
    draw_line(screen_border,1,screen_border,screen_height-1);

    // Draw tangent
    for(angle=0;angle<360;angle++)
        value=cos(angle*1000)*(screen_height/2-20);
        put_pixel( screen_border+angle*(screen_width-screen_border)/360,
                   screen_height/2-value,
                   rgb(255,255,255) );
        // screen_height/2-value because the screen's origin (0,0) is topleft instead of downleft.
    end

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: set_title(), set_mode(), write(), draw_line(), cos(), put_pixel(), key().
