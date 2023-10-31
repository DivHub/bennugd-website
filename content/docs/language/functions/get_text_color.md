---
modules:
- mod_text
title: get_text_color()
---

## Definition

    INT get_text_color( [<INT textID>] )

Gets the current text color (the color where texts will be written in).

## Parameters

- INT `textID`: The [identification code]({{< ref "/docs/language/textid" >}}) of the text (optional parameter, introduced in version rc282).

## Returns

INT: color the text will be written in, or `0` when there is a problem.

## Example

```
Program test;
Global
    my_text;
    text_color;
Begin

    set_text_color( rgb(192,112,0) );
    text_color = get_text_color();

    write    (0,320/2    ,200/2,4,"The color of this text is:");
    write_int(0,320/2+100,200/2,4,&text_color);

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: [`set_text_color()`]({{< ref "/docs/language/functions/set_text_color" >}}), [`write()`]({{< ref "/docs/language/functions/write" >}}), [`write_int()`]({{< ref "/docs/language/functions/write_int" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}).
