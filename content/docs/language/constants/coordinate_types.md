---
title: Coordinate Types
---

Coordinatetype modes are used to set the type of coordinatesytem to be used, by assigning them to the local variable ctype. Different coordinatesystems have different ways of interpreting the coordinates of a process. There's another local variable which influences the interpretation of a process' coordinate, which is resolution.

How to change in which individual scroll or Mode7-view the process is visible, see cnumber and its constants. [Coordinate Numbers]({{< ref "/docs/language/constants/coordinate_numbers" >}}).

## List

| Constant | Value | Description |
|---|---|---|
| `C_SCREEN` | 0 | The screen's top left corner, coordinate (0,0). |
| `C_SCROLL` | 1 | The foreground graphic of the scroll in which the process is shown. |
| `C_M7` | 2 | The main graphic of the Mode7-view. |
{.table}
