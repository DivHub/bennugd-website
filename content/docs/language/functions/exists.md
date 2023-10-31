---
modules:
- mod_proc
title: exists()
---

## Definition

    INT Exists ( <INT processID|processTypeID> )

Checks if a [process](#) is alive, using its [processID](#) or checks if there is a process alive of a certain [processType](#), using its [processTypeID](#).

## Parameters

- INT processID|processTypeID - The ProcessID of the process or the ProcessTypeID of the type of processes to be checked.

## Returns

INT : The result of the check

- `0` (false) - The process with given processID is not alive or there are no processes alive of the given processTypeID.
- `1` (true)  - The process with given processID is alive or there is at least one process alive of the given processTypeID.


## Example

```
import "mod_proc"
import "mod_say"

Process Main()
Begin

    Proc();

    if(exists(id))
        say("I exist! (id)");
    end

    if(exists(0))
        say("0 exists!");
    else
        say("0 doesn't exist!");
    end

    if(exists(type proc))
        say("1- Proc exists!");
    else
        say("1- Proc doesn't exist!");
    end

    let_me_alone();

    if(exists(type proc))
        say("2- Proc exists!");
    else
        say("2- Proc doesn't exist!");
    end

End

Process Proc()
Begin
    Loop
        frame;
    End
End
```

Used in example: [`exists()`]({{< ref "/docs/language/functions/exists" >}}), [`say()`]({{< ref "/docs/language/functions/say" >}}), [`let_me_alone()`]({{< ref "/docs/language/functions/let_me_alone" >}}).
