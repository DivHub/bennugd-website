---
title: Text
---

A *text* is a text written on screen with texts functions, like [`write()`]({{< ref "/docs/language/functions/write" >}}) or [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}). A text is addressed using the associated [`TextID`]({{< ref "/docs/language/textid" >}}).

There are two kinds of texts:

- **Static text** is any text written with [`write()`]({{< ref "/docs/language/functions/write" >}}); it is static, because the content of the text cannot be changed after writing, but the text can be moved and deleted.

- **Dynamic text** is any text written with `write_xxx()` functions; it is dynamic because the content of the text always reflects the current value of the variable specified. Of course moving and deleting is also possible.

## Writing Texts

There are multiple ways to write texts: the [`write()`]({{< ref "/docs/language/functions/write" >}}) function, `write_xxx()` functions and the [`write_in_map()`]({{< ref "/docs/language/functions/write_in_map" >}}) function. With the first two, some the global variable `text_z` is important and with all three of them, the following are important:

- The functions [`set_text_color()`]({{< ref "/docs/language/functions/set_text_color" >}}) and [`get_text_color()`]({{< ref "/docs/language/functions/get_text_color" >}})
- The font
- The [alignment]({{< ref "/docs/language/constants/alignment" >}})
- The global variable `text_flags`

Also the function [`move_text()`]({{< ref "/docs/language/functions/move_text" >}}) can be handy, as it moves a previously written text to a different location.

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

    // Init text settings:
    text_z = 0;
    text_flags = 0;
    set_text_color(rgb(255,255,255));

    // Write some texts
    textid[0] = write(0,0,0,0,"FPS:");
    textid[1] = write_int(0,30,0,0,&fps);
    textid[2] = write_string(0,160,95,1,&str);
    textid[3] = write_float(0,160,105,0,&flt);

    // Show z workings
    set_text_color(rgb(50,150,150));
    textid[4] = write(0,20,20,0,"Underlying text");
    text_z = -1;
    set_text_color(rgb(255,255,255));
    textid[5] = write(0,22,22,0,"On top text");

    // Update the texts until ESC is pressed
    Repeat
        // Notice the texts get updated as the values of str and flt changes.
        // The same goes for the value of fps.
        str = "This program is running for " + time()/100 + " seconds.";
        flt = (float)time()/100;
        frame;
    Until(key(_esc));

    // Delete the texts (this section would be good for OnExit)
    for(x=0; x<maxtexts; x++)
        if(textid[x]!=0)
            delete_text(textid[x]);
        end
    end

End
```

Used in example: [`set_fps()`]({{< ref "/docs/language/functions/set_fps" >}}), [`set_text_color()`]({{< ref "/docs/language/functions/set_text_color" >}}), [`write()`]({{< ref "/docs/language/functions/write" >}}), [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}), [`write_string()`]({{< ref "/docs/language/functions/write_string" >}}), [`write_float()`]({{< ref "/docs/language/functions/write_float" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), [`delete_text()`]({{< ref "/docs/language/functions/delete_text" >}}), text_z, text_flags, fps
