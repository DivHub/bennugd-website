---
modules:
- mod_proc
title: signal()
---

## Definition

    INT signal ( <INT processID|processTypeID> , <INT signal> )

Allows a [process](#)/[function](#) or a range of processes/functions of certain [processType](#) to be controlled in a limited number of ways, by sending [signals](#).

## Parameters

- INT [processID](#)|[processTypeID](#) - The ProcessID of the process or the ProcessTypeID of the type of processes to send the signal to.
- INT signal  - The [signal](#) that is to be sent to the target process(es).

## Returns

INT :

- `false` - The specified processID|processTypeID was ALL_PROCESS or a processTypeID.
- `true`  - The specified processID|processTypeID was a processID.

## Errors

Invalid signal  - The specified signal is invalid.

## Notes

To obtain the processType of a function, the operator Type can be used. For a process to send a signal to itself, the local variable id can be used. The parameter signal is passed by way of a set of signals which denote the signal to be sent. The parameter signal is one of the listed signals. To kill all processes at once, except the calling one, use let_me_alone().

To send a signal to all processes at once, except the calling one, use `signal(ALL_PROCESS,signal)`.

To specify how a process reacts on an incoming signal, use [`signal_action()`]({{< ref "/docs/language/functions/signal_action" >}}).

A signal is carried out immediately, but this does not mean execution of processes is switched to the process, if you just woke it up. This can be achieved by using `frame(0);` after the signal. A frame will cause Bennu to continue execution with the process having the lowest frame-percentage done and it will only continue execution with the current process after all other processes have had their turn. Moreover, using a frame-percentage of 0 will make sure there is nothing added to the done frame-percentage of the process, meaning it doesn't affect the framerate of the process.

## Example

```
signal( get_id(type enemy) , s_kill ); // Kills a process of type enemy.
                                       // Becareful! If there is no enemy process alive,
                                       // get_id() will return 0, which means signal()
                                       // will signal all processes.

signal( id , s_kill_tree );            // Kills the process that calls it, and all of its descendants

signal( Type player , s_freeze );      // Freezes all processes of type player so that they are
                                       //     still displayed, but do not execute any code.

signal(ALL_PROCESS,s_freeze);          // Freezes all processes except the one that called it.
                                       // Can be used to pause a game.

signal( someID , S_WAKEUP ); frame(0); // Wake up the process someID and let it execute once
                                       // (if not done this frame) before continuing.
```
