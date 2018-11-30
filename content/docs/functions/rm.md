---
title: rm()
layout: function
categories:
- functions
divlikes:
- bennugd
module: mod_dir
---

## Definition

    INT rm ( <STRING filename> )

Removes (deletes) the file specified with filename.

## Parameters

STRING filename - The name of the file to be removed (deleted).

## Returns

INT : Success

- `0` (false) - Removing the file with the specified name failed.
- `!0` (true)  - Removing the file with the specified name succeeded.

## Example