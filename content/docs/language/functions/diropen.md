---
modules:
- mod_dir
title: diropen()
---

## Definition

    INT diropen ( <STRING folder> )

Open a directory for read it, returns handle id.

## Parameters

- STRING folder - The folder to open for read.

## Returns

(INT) The handle of the opened directory.

- `0` There was an error.
- `>0` The handle of the opened directory.
