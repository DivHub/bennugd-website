---
modules:
- mod_math
title: isnan()
---

## Definition

    INT isnan ( <FLOAT number> )

Checks if a given value is a number.

It does not check for infinties, use the `isinf()` function for that.

## Parameters

- FLOAT number - The value to check.

## Returns

INT : The result of the check

- `0` (false) - The value is a number.
- `!0` (true)  - The value is NOT a number.
