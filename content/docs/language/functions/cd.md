---
modules:
- mod_dir
title: cd()
---

## Definition

    STRING cd ( [<STRING folder>] )

Sets the current path of execution if folder was specified and returns it.

Note that it is highly recommended to use [`chdir()`]({{< ref "/docs/language/functions/chdir" >}}) for changing the current path of execution, as `cd()` will make Bennu crash when a folder is specified and the returned path of execution is used in the Bennu program. Just using `cd()` without a folder is not a problem.

## Parameters

- STRING folder - The folder to be entered from the current path of execution or a new path of execution.

## Returns

## Example

```
```
```
import "mod_dir"
import "mod_say"
import "mod_key"

Process Main()
Begin

    say(cd());
    say(chdir(".."));
    say(cd());

    Repeat
        frame;
    Until(key(_ESC))

End
```

Used in example: [`cd()`]({{< ref "/docs/language/functions/cd" >}}), [`chdir()`]({{< ref "/docs/language/functions/chdir" >}}), [`say()`]({{< ref "/docs/language/functions/say" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}})
