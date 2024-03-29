---
modules:
- mod_proc
title: get_id()
---

## Definition

    INT get_id ( <INT processTypeID> )

Returns a [ProcessID](#) of a [process](#) of the specified [ProcessType](#). On the next call of `get_id()` in the same process and in the same [frame](#), the next process will be returned of the given type. After a frame statement, `get_id()` is reset and will return the first process of the given processType. When there are no more processes of a given type, which have not been returned, it will return `0`.

`get_id(0)` returns processes of any type.

## Parameters

- INT processTypeID - The [ProcessTypeID](#) of the [ProcessType](#) to get the processes' [ProcessID](#) of.

## Returns

INT : The [ProcessID](#) of a [process](#) of the given [ProcessType](#).

- `0` - There are no more processes of the given processType, which have not been returned.
- `>0`  - The processID of a process of the given processType.

## Example

```
Program example;
Begin
    signaltype(type Monkey,s_kill);
End

/**
 * Empty process
 */
Process Monkey()
Begin
End

/**
 * Signals every process of type 't' the signal 'signal'.
 */
Function int signaltype(int t, int signal)
Begin
    while( (x=get_id(t)) ) // while there is an unprocessed process left and store that in 'x'
        signal(x,signal); // signal the process with processID 'x'.
    end
End

// Of course, the very observant of you already noticed that signaltype(my_type,my_signal)
// does the same thing as the function signal(my_type,my_signal), but this is just to
// illustrate the workings.

/**
 * Signals every process the signal 'signal'.
 */
Function int signalall(int signal)
Begin
    while( (x=get_id(0)) ) // while there is an unprocessed process left and store that in 'x'
        signal(x,signal); // signal the process with processID 'x'.
    end
End

// get_id(0) returns a process of any type. This is a possible implementation of a
// function which signals all existing processes. Note that this can be dangerous to use,
// as in some cases you might want one or two processes to stay alive.
```

Used in example: [`signal()`]({{< ref "/docs/language/functions/signal" >}}).
