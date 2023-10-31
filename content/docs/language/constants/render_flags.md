---
title: Render Flags
---

Render flags are [bit flags]({{< ref "/docs/language/bit_flags" >}}) used to specify the mode of rendering, by passing them to the function [`set_mode()`]({{< ref "/docs/language/functions/set_mode" >}}) as the flags parameter. Multiple render flags can be specified using "`|`" (pipe character) for separation.

See also [Graph Modes]({{< ref "/docs/language/constants/graph_modes" >}}).

## List

| Constant | Value | Description |
|---|---|---|
| `MODE_WINDOW` | 0 | Enables window view. |
| `MODE_2XSCALE` | 256 | Doubles the resolution. Edges get smoothed. |
| `MODE_FULLSCREEN` | 512 | Enables fullscreen view. |
| `MODE_DOUBLEBUFFER` | 1024 | Enables using a double buffer for display. Also called `DOUBLE_BUFFER`. |
| `MODE_HARDWARE` | 2048 | Enables writing directly to Video RAM instead of main RAM. Also called `HW_SURFACE`. |
| `MODE_MODAL` | 4096 | Makes the main window a Modal window. |
| `MODE_FRAMELESS` | 8192 | Makes the main window borderless. |
| `MODE_WAITVSYNC` | 16384 | Synchronize with vertical retrace. Also called `WAITVSYNC`. |
{.table}

## More Info

`MODE_HARDWARE` can cause some operations to speed up and some to slow down.

`MODE_DOUBLEBUFFER` can cause frame transitions to be smoother. However, compatibility with `restore_type = partial_restore` is lost!

`MODE_MODAL` causes the main window to stay focused and hold the mouse.
