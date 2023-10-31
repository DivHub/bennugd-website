---
modules:
- mod_text
title: delete_text()
---

## Definition

    INT delete_text ( <INT TextID> )

Deletes a certain text from the screen.

## Parameters

INT `TextID`  - [TextID]({{< ref "/docs/language/text" >}}) of the [Text]({{< ref "/docs/language/text" >}}) to be deleted.

## Returns

INT `true`

## Notes

`delete_text(ALL_TEXT)` deletes all text from the screen.

## Example

```
Program test;
Global
    my_text;
Begin
    my_text = write(0,320/2,200/2,4,"Press space to delete this.");
    Repeat
        if (key(_space))
            if(my_text>0)
                delete_text(my_text);
                my_text = 0;
            end
        end
        Frame;
    Until(key(_esc))
End
```

Used in example: [`write()`]({{< ref "/docs/language/functions/write" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), [`TextID`]({{< ref "/docs/language/textid" >}})
