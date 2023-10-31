---
title: scan_code
---

## Definition

    INT scan_code

`scan_code` is defined in the [`mod_key` module]({{< ref "docs/language/modules/mod_key" >}}) and, in contrast to [`ascii`]({{< ref "/docs/language/variables/ascii" >}}), **it contains the last key pressed**, not the last character.

That means “A” and “a” will have the same `scan_code`, but different `ascii` value.

## Notes

Take a look at the [scancodes]({{< ref "/docs/language/constants/scancodes" >}}) for a complete list.

## Example

```
import "mod_text"
import "mod_key"
import "mod_video"

process main()
begin
    set_mode(640,320);

    write( 0, 60, 10, 0, "Use lower and upper case characters to see the difference");
    write( 0, 60, 20, 0, "between ascii and scan_code.    (ESC to exit)  ");

    write( 0, 60, 40, 0, "ascii: ");
    write_var( 0, 110, 40, 0, ascii);

    write( 0, 26, 50, 0, "scan_code: ");
    write_var( 0, 110, 50, 0, scan_code);

    while ( !key(_esc))
        frame;
    end
end
```

Used in example: [`write()`]({{< ref "/docs/language/functions/write" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), [`set_mode()`]({{< ref "/docs/language/functions/set_mode" >}}), .
