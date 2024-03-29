---
title: Graph Modes
---

Graph modes are used to specify the color depth of the screen and the mode of rendering, by assigning them to the global variable `graph_mode`. This is also achieved by passing them to the parameters depth and flags in the function [`set_mode()`]({{< ref "/docs/language/functions/set_mode" >}}), which is a pretty tidy solution.

## List

[Color Depths]({{< ref "/docs/language/constants/color_depths" >}}) constants:

| Constant | Value | Description |
|---|---|---|
| `MODE_8BITS` | 8 | Use a color depth of 8bit. Also called `MODE_8BPP`. |
| `MODE_16BITS` | 16 | Use a color depth of 16bit. Also called `MODE_16BPP`. |
| `MODE_32BITS` | 32 | Use a color depth of 32bit. Also called `MODE_32BPP`. |
{.table}

[Render Flags]({{< ref "/docs/language/constants/render_flags" >}}) constants:

| Constant | Value | Description |
|---|---|---|
| `MODE_WINDOW` | 0 | Enables window view. |
| `MODE_2XSCALE` | 256 | Doubles the resolution. Edges get smoothed. |
| `MODE_FULLSCREEN` | 512 | Enables fullscreen view. |
| `MODE_DOUBLEBUFFER` | 1024 | Enables using a double buffer for display. Also called `DOUBLE_BUFFER`. |
| `MODE_HARDWARE` | 2048 | Enables writing directly to Video RAM instead of main RAM. Also called `HW_SURFACE`. |
| `MODE_MODAL` | 4096 | Makes the main window a Modal window. |
| `MODE_FRAMELESS` | 8192 | Makes the main window borderless. |
{.table}
