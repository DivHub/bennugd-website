---
modules:
- mod_blendop
title: blendop_identity()
---

## Definition

    INT blendop_identity ( <INT blendopTable> )

Reinitializes the blend table to default.

The source section of the blend table will be the normal object and the destination section will be cleared, removing translucency.

## Parameters

INT blendTable  - The blend table to reinitialize.

## Returns

INT : true
