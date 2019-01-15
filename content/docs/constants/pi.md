+++
categories = ["constants", "math"]
layout = "constant"
modules = ["mod_math"]
title = "PI"

+++

## Definition

    INT PI == 180000

The equivalent to the mathematical pi (3.14159265...), in thousandths of a degree.

It can be used to define angles, like assigning one to the local variable angle, or passing one to the function [`xadvance()`]({{< ref "/docs/functions/xadvance" >}}).

## Example

```
angle = PI/2; // 90000 (90 degrees)
xadvance(-PI/4,10); // -45000 (-45 degrees)
```
