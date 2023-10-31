---
modules:
- mod_math
title: isinf()
---

## Definition

    INT isinf ( <FLOAT number> )

Checks if a given value is an infinity. This function is the opposite of the `finite()` function.

It does not check for Not-A-Numbers. Use the `isnan()` function for that.

## Parameters

- FLOAT number - The value to check.

## Returns

INT : The result of the check

- `0` (false) - The value is a not an infinity.
- `!0` (true)  - The value is a positive or negative infinity.

## See also

Wikipedia page about the mathematical subject [infinity](https://en.wikipedia.org/wiki/Infinity).
