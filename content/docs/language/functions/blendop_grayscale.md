---
modules:
- mod_blendop
title: blendop_grayscale()
---

## Definition

    INT blendop_grayscale ( <INT blendTable> , <INT mode> )

Modify the [blend table]({{< ref "blend_operations" >}}) by modifying the colours, so the compononts of one colour is the same (this makes them appear gray). This means that the graphic the blend operation is assigned to will appear gray.

The source section of the [blend table]({{< ref "blend_operations" >}}) will be modified; this will clear the destination section of the blend table.

## Parameters

- INT blendTable - The blend table to modify.
- INT mode - The mode to perform the grayscaling (see notes).

## Returns

INT : true

## Modes

Method 1

    component = 0.3*r+0.59*g+0.11*b;
    colour = rgb ( component , component , component )

Method 2

    max = r > g ? r > b ? r : g : g > b ? g : b;
    min = r < g ? r < b ? r : g : g < b ? g : b;
    component = ( max + min ) / 2 colour = rgb ( component , component , component )

Method 3

    max = r > g ? r > b ? r : g : g > b ? g : b;
    colour = rgb ( max , max , max )
