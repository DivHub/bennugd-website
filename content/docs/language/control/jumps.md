---
title: Jumps
---

## `Call` Command

    call <label> ; 

The `call` command jumps to the given label inside a [function]({{< ref "docs/language/keywords/function" >}}) or [process]({{< ref "docs/language/keywords/process" >}}) until it comes across a return statement. When this happens, it jumps back to call statement and resumes after it. 

## `Jmp` Command

    jmp <label> ; 

The `jmp` command jumps to the given label inside a [function]({{< ref "docs/language/keywords/function" >}}) or [process]({{< ref "docs/language/keywords/process" >}}). Unlike the `call` command, there is nothing more to it. 

## Example

```
import "mod_say"

Process Main()
Begin

    say(my_function(1));

End

Function my_function(int value)
Private
    int ret;
Begin

    Jmp real_begin;

jumping:
    ret = 300;
    return;

real_begin:
    ret = 100;
    if(value == 1)
        Call jumping;
    end
    ret += 200;
    return ret;

End
```

The output of this example is 500, when `value` is 1. This example show 500 because the input value is a one and it causes that goes to the jumping label inserting a 300 and adding a 200 after.
