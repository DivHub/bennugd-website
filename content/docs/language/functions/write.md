---
modules:
- mod_text
title: write()
---

## Definition

    INT write ( <INT fontID> , <INT x> , <INT y> , [<INT z>] , <INT alignment> , <STRING text>)

Puts a dynamic [`text`]({{< ref "/docs/language/text" >}}) with a certain font on certain coordinates on the screen with a certain [alignment]({{< ref "/docs/language/constants/alignment" >}}).

## Parameters

- INT `fontID` - The FontID of the font to be used for the text.
- INT `x` - The X coordinate of the text.
- INT `y` - The Y coordinate of the text.
- INT `z` - The depthplane of the text (optional, introduced in version rc282).
- INT `alignment` - The type of [alignment]({{< ref "/docs/language/constants/alignment" >}}).
- STRING `text` - The text to be used.

## Returns

INT: [`TextID`]({{< ref "/docs/language/textid" >}})

- `-1`  - Error. The text could not be obtained or was empty.
- `>=0` - The [`TextID`]({{< ref "/docs/language/textid" >}}) of the text.

## Notes

There is a limit of 511 texts to simultaneously exist on the screen. The program will crash with an error when this number is reached.

The text depth can be changed by adjusting the global variable text_z.

To write variables to the screen, rather use [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}), [`write_string()`]({{< ref "/docs/language/functions/write_string" >}}), [`write_float()`]({{< ref "/docs/language/functions/write_float" >}}) or [`write_var()`]({{< ref "/docs/language/functions/write_var" >}}) than this command.

To write text on a map you can use the command [`write_in_map()`]({{< ref "/docs/language/functions/write_in_map" >}}).

If you write texts with a font and you change any symbol of this font after, all written texts will be updated using the new changed symbols.

## Example

```
Program texts;
Const
    maxtexts = 10;
Private
    int textid[maxtexts-1];
    string str;
    float flt;
Begin

    // Set FPS
    set_fps(60,0);

    // Write some texts
    textid[0] = write(0,0,0,0,"FPS:");
    textid[1] = write_int(0,30,0,0,&fps);
    textid[2] = write_string(0,160,95,1,&str);
    textid[3] = write_float(0,160,105,0,&flt);

    // Update the texts until ESC is pressed
    Repeat
        // Notice the texts get updated as the values of str and flt changes.
        // The same goes for the value of fps.
        str = "This program is running for " + timer/100 + " seconds.";
        flt = (float)timer/100;
        frame;
    Until(key(_esc));

    // Delete the texts
    for(x=0; x<maxtexts; x++)
        if(textid[x]!=0)
            delete_text(textid[x]);
        end
    end

End
```

Used in example: [`set_fps()`]({{< ref "/docs/language/functions/set_fps" >}}), [`write()`]({{< ref "/docs/language/functions/write" >}}), [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}), [`write_string()`]({{< ref "/docs/language/functions/write_string" >}}), [`write_float()`]({{< ref "/docs/language/functions/write_float" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), [`delete_text()`]({{< ref "/docs/language/functions/delete_text" >}}), array, fps, [`TextID`]({{< ref "/docs/language/textid" >}})
