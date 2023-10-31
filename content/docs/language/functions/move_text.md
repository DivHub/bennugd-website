---
modules:
- mod_text
title: move_text()
---

## Definition

    INT move_text ( <INT TextID> , <INT x> , <INT y>, <INT z>)

Moves an existing [text]({{< ref "/docs/language/text" >}}) to another place on the screen. The alignment of the text is defined by it's [alignment mode]({{< ref "/docs/language/constants/alignment" >}})

## Parameters

- INT `TextID` - [Identifier]({{< ref "/docs/language/textid" >}}) of the text you want to move. This identifier should have been appointed to a text earlier on.
- INT `x` - The new horizontal coordinate (of the control point) of your text.
- INT `y` - The new vertical coordinate (of the control point) of your text.
- INT `z` - The new depthplane (of the control point) of your text. (introduced in version r282)

## Returns

INT: `true`

## Example

```
Program test;
Global
    My_text;
Begin
    My_text=write(0,320/2,200/2,4,"Press space to move this.");
    Loop
        If (key(_space))
            Move_text(My_text,rand(0,319),rand(0,199));
        End
        Frame;
    End
End
```

Used in example: write(), key(), rand().

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

Used in example: write(), write_int(), key(), rand(), set_mode(), set_text_color().
