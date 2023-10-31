---
modules:
- mod_effects
title: Blur Modes
---

Blur modes are used to specify the mode of blurring in the [`blur()`]({{< ref "/docs/language/functions/blur" >}}).

## List

| Constant | Value | Description |
|---|---|---|
| `BLUR_NORMAL` | 0 | single pixel: considers pixels located to the left and above of each pixel. |
| `BLUR_3X3` | 1 | 3x3: considers all 8 adjacent pixels. |
| `BLUR_5X5` | 2 | 5x5: considers the 24 pixels that surrounds each pixel. |
| `BLUR_5X5_MAP` | 3 | 5x5 with additional map: Just as the previous one but using a temporary map. |
{.table}
