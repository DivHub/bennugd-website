---
title: Scale Modes
---

Scale modes are used to set the mode of scaling, by assigning one of them to the global variable `scale_mode`.

## List

| Constant | Value | Description |
|---|---|---|
| `SCALE_NONE` | 0 | No scale. |
| `SCALE_SCALE2X` | 1 | Scale two times; use some filter. Looks like [`MODE_2XSCALE`]({{< ref "/docs/language/constants/graph_modes" >}}). |
| `SCALE_HQ2X` | 2 | Scale two times; use HQ filter. Looks nice, runs slower. |
| `SCALE_SCANLINE2X` | 3 | Scale two times; use scanline filter. |
| `SCALE_NORMAL2X` | 4 | Scale two times; no extra filter. Also called `SCALE_NOFILTER`. |
{.table}
