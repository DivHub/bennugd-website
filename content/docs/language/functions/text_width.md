---
modules:
- mod_text
title: text_width()
---

## Definition

    INT text_width ( <INT fontID> , <STRING text> )

Calculates the width in pixels of the specified text in the specified font.

## Parameters

- INT `FontID` - FontID of the font for which the width of the text will be the calculated.
- STRING `text` - The text of which the width will be calculated.

## Returns

INT: The width in pixels of the text in the font.

- `0` - Invalid or no text; invalid font.
- `>0` - The width in pixels of the text in the font.

## See Also

- [`text_height()`]({{< ref "/docs/language/functions/text_height" >}})
