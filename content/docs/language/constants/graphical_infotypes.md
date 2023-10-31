---
title: Graphical Infotypes
---

Graphical infotypes are used in [`graphic_info()`]({{< ref "/docs/language/functions/graphic_info" >}}), to specify what information about a graph is wanted.

## List

| Constant | Value | Description |
|---|---|---|
| `G_WIDTH` | 0 | Width in pixels. `G_WIDE` is equivalent, but deprecated. |
| `G_HEIGHT` | 1 | Height in pixels. |
| `G_X_CENTER` | 2 | X-axis center. Also called `G_CENTER_X` |
| `G_Y_CENTER` | 3 | Y-axis center. Also called `G_CENTER_Y` |
| `G_PITCH` | 4 | Width in bytes. |
| `G_DEPTH` | 5 | Color depth in bits per pixel. |
| `G_FRAMES` | 6 | Number of frames. |
| `G_ANIMATION_STEP` | 7 | Current frame in animation. |
| `G_ANIMATION_STEPS` | 8 | Number of frames in animation. |
| `G_ANIMATION_SPEED` | 9 | Current speed of animation. |
| `B_CLEAR` | 1 | Used in function [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), indicates if a bitmap is cleared. |
| `CHARSET_ISO8859` | 0 | Used to select `iso8859` character set in the function [`fnt_new()`]({{< ref "/docs/language/functions/fnt_new" >}}). |
| `CHARSET_CP850` | 1 | Used to select `cp850` character set in the function [`fnt_new()`]({{< ref "/docs/language/functions/fnt_new" >}}). |
| `NFB_VARIABLEWIDTH` | 0 | Flag for the function [`fnt_new()`]({{< ref "/docs/language/functions/fnt_new" >}}). |
| `NFB_FIXEDWIDTH` | 1 | Flag for the function [`fnt_new()`]({{< ref "/docs/language/functions/fnt_new" >}}). |
{.table}
