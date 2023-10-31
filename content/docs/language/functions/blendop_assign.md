---
modules:
- mod_blendop
title: blendop_assign()
---

## Definition

    INT blendop_assign ( <INT fileID> , <INT graphID> , <INT blendTable> )

Assigns a [blend operation]({{< ref "blend_operations" >}}) to a graphic. The graphic will be drawn using this blend operation hereafter. Only one blend operation can be assigned to one graphic at a given time; when another is assigned, the previous one is unassigned.

To deassigning a [blend table]({{< ref "blend_operations" >}}), using [`NULL`]({{< ref "/docs/language/constants/null" >}}) as the blendopID.

## Parameters

- INT fileID - The fileID of the file holding the graphic.
- INT graphID - The graphID of the graphic to assign the blendop to.
- INT blendTable - The blend table to assign (NULL for none).

## Returns

INT : true
