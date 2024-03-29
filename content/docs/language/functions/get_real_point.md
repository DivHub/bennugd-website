---
modules:
- mod_grproc
title: get_real_point()
---

## Definition

    INT get_real_point( <INT controlpoint> , <INT POINTER x> , <INT POINTER y> )

Finds the actual position on the screen of the calling process, given its graphic and the specified _control point_ on this graphic. All process-related variables are taken into account, like `x`, `y`, `angle`, even `ctype`. These coordinates are then assigned to the variables pointed to by `x` and `y`.

## Parameters

- INT controlpoint - The controlpoint on the process' graphic of which the actual position is wanted.
- INT POINTER x - A pointer to an integer to which the X-coordinate will be assigned.
- INT POINTER y - A pointer to an integer to which the Y-coordinate will be assigned.

## Returns

INT : Successrate

- `false` - Error: no graphic; invalid controlpoint;
- `true` - Success.
