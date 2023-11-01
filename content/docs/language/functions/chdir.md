---
modules:
- mod_dir
title: chdir()
---

## Definition

    INT chdir ( <STRING directoryname> )

Sets the current path of execution.

## Parameters

- STRING directoryname - The name of the directory to be entered from the current path of execution or a new path of execution.

## Returns

INT : Success

- `0` - Setting of current path of execution succeeded.
- `!0` - Setting of current path of execution failed.

## Example

```
import "mod_dir"
import "mod_say"
import "mod_key"

Process Main()
Begin

    say(CD());
    ChDir("..");
    say(CD());

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: [`cd()`]({{< ref "/docs/language/functions/cd" >}}), [`chdir()`]({{< ref "/docs/language/functions/chdir" >}}), [`say()`]({{< ref "/docs/language/functions/say" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}})
