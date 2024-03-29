---
title: Process
---

    Process <name> ( [ <parameters> ] )
    [ Public
        [ <public variables> ]
    ]
    [ Private
        [ <private variables> ]
    ]
    Begin
        [ <main code> ]
    [OnExit
        [ <OnExit code> ]
    ]
    End

`Process` is a reserved word used to start the code of a process. If name is *Main*, that process will be started at the start of the program.

A process is a subroutine to which one or more of the following apply:

- it receives parameters
- it acts on the parameters
- it processes data located elsewhere

In addition to these possibilities, a process always has a frame; statement. The difference between a function and a process is a process is treated as a separate thread. This means one can't let a process return a value like a function, as the father process continues its code as well, as soon as the process hits a frame; statement or when the code is done. When that happens, the process 'returns' its ProcessID and continues the code (in the next frame).

When the frame; statement is reached in the code, a number of other local variables are defined or updated not only of the new process, but also of related processes. These are:

- The [`father`]({{< ref "father" >}}) variable of the new process.
- The [`son`]({{< ref "son" >}}) variable of the father process (updated).
- The [`bigbro`]({{< ref "bigbro" >}}) variable of the new process.
- The [`smallbro`]({{< ref "smallbro" >}}) variable of the processes called by the father immediately before the new process was called (updated).
- The son and smallbro variables are also defined of the new process, but do not yet carry values.

When there are no more processes alive, the program ends.

## Local variables as parameters

When a process is declared with parameters that are actually local variables, arguments for these parameters will initialise those local variables. This may sound strange, but an example will clear things up.

For example, consider the local variables x, y, z, file and graph. To create a process to move a game sprite around, you can declare it as follows:

```
process Ship (x,y,z,file,graph)
begin
    // move left 1 pixel per frame
    repeat
        x -= 1; // move 1 pixel to the left
        frame; // this process is done for this frame, wait for the next
    until (x<0);
end
```

Calling the process with e.g. Ship(300,100,5,0,1); will have the Ship appear at the coordinates (300,100) on Z-Level 5 with the Sprite No.1 in the file number 0. The ship will move left until it leaves the screen. You can change movement by changing the x/y value of the process and animate the ship by changing the graph value.

## Example

```
Process SpaceShip( int x, int y, int angle, int maxspeed, int maxturnspeed)
Public // Declare public variables here
Private // Declare private variables here
    int speed;
Begin // Start the main processcode
    graph = new_map(20,20,8);
    map_clear(0,graph,rgb(0,255,255));
    Loop
        speed+=key(_up)*(speed<maxspeed)-key(_down)*(speed>-maxspeed);
        angle+=(key(_left)-key(_right))*maxturnspeed;
        advance(speed);
        frame;
    End
OnExit // Start the exit code
    unload_map(0,graph);
End // End the main processcode

Now one can call this process for example by doing the following.

Process Main()
Begin
    SpaceShip(100,100,0,20,5000);
    Repeat
        frame;
    Until(key(_ESC))
    let_me_alone();
End
```

Used in example: [`new_map()`]({{< ref "map_new" >}}), [`map_clear()`]({{< ref "map_clear" >}}), [`key()`]({{< ref "key" >}}), [`advance()`]({{< ref "advance" >}}), [`unload_map()`]({{< ref "map_unload" >}}), [`let_me_alone()`]({{< ref "let_me_alone" >}}), Process, Begin, End, Loop, Repeat, graph, angle

And when the SpaceShip process ends - because the code of it reached the End or something sent an s_kill signal - the OnExit code starts. In this example it will unload the memory used for the created graphic. If there is no OnExit code, the process will just end.

This will make a SpaceShip with a cyan coloured block, able to move around the screen.


