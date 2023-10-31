---
modules:
- mod_text
title: set_text_color()
---

## Definition

    INT set_text_color ( [INT < textID>] , <WORD color> )

Sets the current text color (the color where texts will be written in). This only affects 1 bit (2 color) fonts, which can be loaded with load_font() or load_bdf(). 8 bit and 16 bit fonts already contain color information themselves and thus aren't affected.

## Parameters

- INT `textID` - [TextID]({{< ref "/docs/language/text" >}}) of the text (optional).
- WORD `color` - The color to use for text.

## Returns

*(Needs confirmation.)*

INT: Result.

- `true` if successful
- `false` if failed.


> VOID: in version rc282 this function returns nothing.

## Notes

Be warned that values returned by the [`rgb()`]({{< ref "/docs/language/functions/rgb" >}}) function differ with the video card. So, directly filling out color numbers as color parameter in 16 bit color mode without using [`rgb()`]({{< ref "/docs/language/functions/rgb" >}}) is a bad idea, as [`rgb()`]({{< ref "/docs/language/functions/rgb" >}}) returns the correct color code for every video card

The optional argument textID is fairly new. It is introduced in version rc282.

## Example

```
Program awesome;
Global
    byte red=0;
    byte green=255;
    byte blue=0;

Begin

    set_text_color(rgb(red,green,blue));
    write(0,1,1,0,"Mijn potlood is bruin"); //this text will be green as an Irishman's ejecta

    set_text_color(rgb(255,0,0));
    write(0,1,11,0,"Je moeder"); //this text will be red

    Loop

        frame;
    End
End
```

Used in example: write(), rgb().

## Example 2

```
import "mod_text";
import "mod_mouse";
import "mod_key";
import "mod_video";
import "mod_rand";
import "mod_map";

private
    txt[10];
    counter;
    tz;
begin
    set_mode(640,480,32);

    txt[0]=write_int(0,10,10,10,0,&counter);
    txt[1]=write_int(0,10,20,-5,0,&tz);
    txt[2]=write(0,10,10,0,0,"hello world");

    set_text_color(txt[1], rgb(255,0,0));


    while(!key(_ESC))

        counter++;

        move_text(txt[2], mouse.x, mouse.y, tz );

        set_text_color(txt[0], rand(0101010h, 0ffffffh));

        if ( key( _DOWN ) ) tz--; end
        if ( key( _UP ) ) tz++; end

        frame;
    end
end
```

Used in example: write(), write_int(), rgb(), key(), set_mode(), move_text().
