---
title: rmdir()
layout: function
categories:
- functions
divlikes:
- bennugd
module: mod_dir
---

## Definition

    INT rmdir ( <STRING directoryname> )

Removes (deletes) the directory in the current path of execution with a certain name.

## Parameters

STRING directoryname  - The name of the directory to be removed (deleted).

## Returns

INT : Success

- `0` (false) - Removing the directory with the specified name failed.
- `!0` (true)  - Removing the directory with the specified name succeeded.