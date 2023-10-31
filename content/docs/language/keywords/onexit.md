---
title: OnExit
---

    Begin
        [ <main code> ]
    [OnExit
        [ <exit code> ]
    ]
    End

The OnExit statement can be used between the Begin and End statements in the Process or Function. When the Program, Process or Function is killed, the exit code starts. This can be easily used to free any memory used by the exiting process.

## Notes

Be advised, Frame statements are interpreted as Frame(0) statements, to ensure exit code of the killed instance finishes the same frame as the instance is killed. Code like

    Loop frame; End

will cause Bennu to freeze, as `frame(0);` doesn't allow switching to another instance.

## Example

### Basic Example

```
import "mod_proc"
import "mod_say"

Process proc1()
Begin // Start the main code part of the process
    say("Proc created");

    // Run indefinitely (or until killed)
    Loop
        frame;
    End
OnExit // Start the exit code of the process
    say("Proc killed!");
End

Function int func1()
Begin // Start the main code part of the function
    say("Func created");
    return 0;
OnExit // Start the exit code of the function
    say("Func killed!");
End

Process Main()
Private
    int p;
Begin // Start the main code part of the main process
    p = proc1(); // create new instance of proc1
    func1();
    say("Main is here");
OnExit // Start the exit code of the main process
    say("Main is killed");
    signal(p,S_KILL);
    say("Main is at the end");
End
```

Used in example: loop, end, process, function, frame, say()

Resulting console messages:

```
Proc created
Func created
Func killed!
Main is here
Main is killed
Main is at the end
Proc killed!
```

### Resource Cleanup

A good use for this is the following:

```
Process ship()
Begin
    graph = map_new(20,20,8);
    Loop frame; End
OnExit
    map_unload(0,graph);
End
```

Used in example: map_new(), map_unload(), graph, loop, frame, end
