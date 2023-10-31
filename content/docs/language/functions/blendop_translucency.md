---
modules:
- mod_blendop
title: blendop_translucency()
---

## Definition

    INT blendop_translucency ( <INT blendTable> , <FLOAT amount> )

Modify the [blend table]({{< ref "blend_operations" >}}) by setting how much the object is visible and how much what is behind the source. This means that the graphic the blend operation is assigned to will appear translucent or transparent.

This will modify both the source and destination section of the [blend table]({{< ref "blend_operations" >}}). The source is multiplied by amount and the destination is multiplied by `1-amount`.

## Parameters

- INT blendTable - The blend table to modify.
- FLOAT amount - Opacity factor ( 1 (opaque) - 0 (transparent) ).

## Returns

INT : true

## Notes

To set an amount of `0.5` is the same as doing using a [blit flag]({{< ref "blit_flags" >}}) of `B_TRANSLUCENT`.
