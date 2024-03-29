---
title: Coordinate Numbers Flags
---

Coordinatenumber flags are used to set which scroll or mode_7 coordinate system should display a process, by assigning them to the local variable cnumber of that process. This only has influence on scrolls or mode_7 coordinate systems, not on the screen's coordinate system.

How to change the used coordinate system, see ctype and its constants. [Coordinate Types]({{< ref "/docs/language/constants/coordinate_types" >}}).

## List

| Constant | Value | Description |
|---|---|---|
| | 0 | Display the process in all scroll/mode_7-views (**default**). |
| `C_0` | 1 | Display the process in the scroll/mode_7-view with ID 0. |
| `C_1` | 2 | Display the process in the scroll/mode_7-view with ID 1. |
| `C_2` | 4 | Display the process in the scroll/mode_7-view with ID 2. |
| `C_3` | 8 | Display the process in the scroll/mode_7-view with ID 3. |
| `C_4` | 16 | Display the process in the scroll/mode_7-view with ID 4. |
| `C_5` | 32 | Display the process in the scroll/mode_7-view with ID 5. |
| `C_6` | 64 | Display the process in the scroll/mode_7-view with ID 6. |
| `C_7` | 128 | Display the process in the scroll/mode_7-view with ID 7. |
| `C_8` | 256 | Display the process in the scroll/mode_7-view with ID 8. |
| `C_9` | 512 | Display the process in the scroll/mode_7-view with ID 9. |
{.table}
