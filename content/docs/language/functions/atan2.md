---
modules:
- mod_math
title: atan2()
---

## Definition

    FLOAT atan2 ( <FLOAT y> , <FLOAT x>)

Returns the arctangent of a certain value. It is computed as the arc tangent of `y/x`. The signs of the arguments are used to perform the calculation.

This function performs an arctangent calculation on a certain value and returns an [angle]({{< ref "angle" >}}) between but not including -180000 and 180000 (-180-180º).

## Parameters

- FLOAT y - The Y value to be performed an arctangent calculation on.
- FLOAT x - The X value to be performed an arctangent calculation on.

## Returns

FLOAT : The arctangent result of the specified value, an angle between but not including -180000 and 180000 (-180-180º).

## Notes

The angle value returned by this function is in thousandths of degrees, as most angles within Bennu are.

To read about all aspects of trigonometry, you can visit Wikipedia's [Trigonometric functions](https://en.wikipedia.org/wiki/Trigonometric_functions) and [atan2](https://en.wikipedia.org/wiki/Atan2) pages.

## See also

 - [`atan()`]({{< ref "/docs/language/functions/atan" >}})
