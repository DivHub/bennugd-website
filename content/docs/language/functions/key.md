---
modules:
- mod_key
title: key()
---

## Definition

    INT key( <INT scancode> )

Checks if a certain key is being pressed.

## Parameters

- INT scancode - The scancode of the key to be checked.

## Returns

INT : `true`/`false`: Whether the key is being pressed.

## Notes

Take a look at the [scancodes]({{< ref "/docs/language/constants/scancodes" >}}) for a complete list.

## Example

This will output the words `LEFT` or `RIGHT` according to the keys you press, or it will quit the program once ESCAPE is pressed.

```
Program input_test;
Begin

    While( !key(_esc) )

        delete_text(ALL_TEXT);

        if( key(_left) && !key(_right) )
            write(0,160,120,4, "LEFT");
        end;

        if( key(_right) && !key(_left) )
            write(0,160,120,4, "RIGHT");
        end;

        frame;

    End;

    exit();

End
```

Used in example: [`delete_text()`]({{< ref "/docs/language/functions/delete_text" >}}), [`write()`]({{< ref "/docs/language/functions/write" >}}), [`exit()`]({{< ref "/docs/language/functions/exit" >}}), ALL_TEXT
