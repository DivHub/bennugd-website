---
modules:
- mod_math
title: atan()
---

## Definition

    FLOAT atan ( <FLOAT value> )

Returns the arctangent of a certain value.

This function performs an arctangent calculation on a certain value and returns an [angle]({{< ref "angle" >}}) between but not including -90000 and 90000 (-90-90º).

## Parameters

- FLOAT value - The value to be performed an arctangent calculation on.

## Returns

FLOAT : The arctangent result of the specified value, an angle between but not including -90000 and 90000 (-90-90º).

## Notes

The angle value returned by this function is in thousandths of degrees, as most angles within Bennu are.

To read about all aspects of trigonometry, you can visit Wikipedia's [Trigonometric function](https://en.wikipedia.org/wiki/Trigonometric_functions) page.
