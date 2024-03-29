---
modules:
- mod_blendop
title: blendop_tint()
---

## Definition

    INT blendop_tint ( <INT blendTable> , <FLOAT amount> , <INT r> , <INT g> , <INT b> )

Modify the [blend table]({{< ref "blend_operations" >}}) by tinting the colours with the specified colour. This means that the graphic the blend operation is assigned to will appear more like the specified colour, depending on the amount.

This will modify the source section of the [blend table]({{< ref "blend_operations" >}}), but leave the destination section as it was.

## Parameters

INT blendTable - The blend table to tint.
FLOAT amount - The amount to use the specified colour (0.0 to 1.0).
BYTE r - The red component of the colour to be used for the tinting (0 to 255).
BYTE g - The green component of the colour to be used for the tinting (0 to 255).
BYTE b - The blue component of the colour to be used for the tinting (0 to 255).

## Returns

INT : true

## Example

```
```
