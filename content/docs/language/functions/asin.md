---
modules:
- mod_math
title: asin()
---

## Definition

    FLOAT asin ( <FLOAT value> )

Returns the arcsine of a certain value.

This function performs an arcsine calculation on a certain value and returns an [angle]({{< ref "angle" >}}) between and including -90000 and 90000 (-90-90º).

## Parameters

- FLOAT value - The value to be performed an arcsine calculation on.

## Returns

FLOAT : The arcsine result of the specified value, an angle between and including -90000 and 90000 (-90-90º).

## Notes

The angle value returned by this function is in thousandths of degrees, as most angles within Bennu are.

To read about all aspects of trigonometry, you can visit Wikipedia's [Trigonometric function](https://en.wikipedia.org/wiki/Trigonometric_functions) page.
