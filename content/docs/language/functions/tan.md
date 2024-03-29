---
modules:
- mod_math
title: tan()
---

## Definition

    FLOAT tan ( <FLOAT angle> )

Returns the tangent of a certain [angle]({{< ref "angle" >}}).

This function performs a tangent calculation on a certain angle and returns a value.

## Parameters

FLOAT angle - Angle, in thousandths of degrees. i.e. 75000 = 75º

## Returns

FLOAT : The tangent result of the specified angle.

## Notes

The angle value returned by this function is in thousandths of degrees, as most angles within Bennu are.

To read about all aspects of trigonometry, you can visit Wikipedia's [Trigonometric function](https://en.wikipedia.org/wiki/Trigonometric_functions) page.

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
    set_title("Tangent Graph");
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
        value=tan(angle*1000)*(screen_height/2-20);
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

Used in example: set_title(), set_mode(), write(), draw_line(), tan(), put_pixel(), key()
