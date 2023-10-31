---
modules:
- mod_math
title: acos()
---

## Definition

    FLOAT acos ( <FLOAT value> )

Returns the arccosine of a certain value.

This function performs an arccosine calculation on a certain value and returns an [angle]({{< ref "angle" >}}) between and including 0 and 180000 (0-180º).

## Parameters

- FLOAT value - The value to be performed an arccosine calculation on.

## Returns

FLOAT : The arccosine result of the specified value, an angle between and including 0 and 180000 (0-180º).

## Notes

The angle value returned by this function is in thousandths of degrees, as most angles within Bennu are.

To read about all aspects of trigonometry, you can visit Wikipedia's [Trigonometric function](https://en.wikipedia.org/wiki/Trigonometric_functions) page.
