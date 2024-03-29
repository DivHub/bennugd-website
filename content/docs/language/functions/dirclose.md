---
modules:
- mod_dir
title: dirclose()
---

## Definition

    INT dirclose ( <INT handleId> )

Close a directory using a given handle id obtained with [`diropen()`]({{< ref "/docs/language/functions/diropen" >}}).

## Parameters

- INT handleId  - The handle id of a directory.

## Returns

INT : The handle of the opened directory.

- `0` - There was an error.
- `1` - The directory was closed successfully.
