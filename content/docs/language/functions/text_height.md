---
modules:
- mod_text
title: text_height()
---

## Definition

    INT text_height ( <INT fontID> , <STRING text> )

Calculates the height in pixels of the specified text in the specified font.

## Parameters

- INT `FontID` - FontID of the font for which the height of the text will be the calculated.
- STRING `text` - The text of which the height will be calculated.

## Returns

INT: The height in pixels of the text in the font.

- `0` - Invalid or no text; invalid font.
- `>0` - The height in pixels of the text in the font.

## See Also

- [`text_width()`]({{< ref "/docs/language/functions/text_width" >}})
