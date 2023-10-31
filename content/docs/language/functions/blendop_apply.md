---
modules:
- mod_blendop
title: blendop_apply()
---

## Definition

    INT blendop_apply ( <INT fileID> , <INT graphID> , <INT blendTable> )

Applies a [blend operation]({{< ref "blend_operations" >}}) to the pixels of a graphic, as if it was rendered into a black (color 0) background.

This function actually changes the pixeldata of the graphic.

## Parameters

- INT fileID - The fileID of the file holding the graphic.
- INT graphID - The graphID of the graphic to apply the blend operation to.
- INT blendTable - The blend table to apply.

## Returns

- INT : true
