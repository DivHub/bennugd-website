---
modules:
- mod_blendop
title: blendop_intensity()
---

## Definition

    INT blendop_intensity ( <INT blendTable> , <FLOAT amount> )

Modify the blend table by intensifying the colours. This means that the graphic the blend operation is assigned to will appear darker or lighter than normal.

This will modify the source section of the blend table, but leave the destination section as it was.

## Parameters

- INT blendTable - The blend table to intensify.
- FLOAT amount - The amount to multiply the R,G,B values of the colours by.

## Returns

INT : true
