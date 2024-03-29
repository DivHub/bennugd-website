---
modules:
- mod_proc
title: signal_action()
---

## Definition

    INT signal_action ( [<INT processID|processTypeID> , ] INT signal , INT action )

Sets the reaction of one or more processes when they receive a certain nonforceful-signal. Only existing processes are affected, processes created afterwards are not.

## Parameters

INT processID|processTypeID - A ProcessID,ProcessTypeID or ALL_PROCESS.
INT signal  - The code of a nonforceful-signal for which a reaction is to be specified.
INT action  - The reaction of the process when it receives a signal. (S_DFL/S_IGN)

## Returns

INT : true

## Notes

The reaction to an incoming forced signal (S_KILL_FORCE, S_SLEEP_FORCE, etc) cannot be changed and is S_DFL by default.

## Example

```
// The current process ignores the kill signal from now on
signal_action(S_KILL,S_IGN);

// All currently existing processes ignore the kill signal from now on
signal_action(ALL_PROCESS,S_KILL,S_IGN);

// All currently existing processes of type 'Player' ignore the freeze signal from now on
signal_action(type Player,S_FREEZE,S_IGN);
```
