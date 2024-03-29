---
title: Public Variables
---

A public variable is a variable that is specific to a process or function in the same way as a private variable. Unlike a private variable, however, a public variable can be accessed from the rest of the program, by use of the ProcessID of that process. This ProcessID must be stored in a variable of type ProcessName. It is like a local variable, but just for one ProcessType instead of for all.

Because of the way the compiler works, public variables are only accessible for processes and functions below the declaration (which in fact is pretty normal). To assist in this matter, the statement Declare was created.

To start the declaration of public variables, use [`Public`]({{< ref "docs/language/keywords/public" >}}).

## Example

```
import "mod_say"
import "mod_proc"

Declare Process SpaceShip()
    Public
        int speed = 50;
        String name = "Galactica";
    End
End

Global
    SpaceShip ship;
End

Process Main()
Begin
    ship = SpaceShip();
    say(ship.name + ": " + ship.speed);
    signal(ship,S_KILL);
End

Process SpaceShip()
Begin
    Loop
        frame;
    End
End
```

Used in example: say(), key(), signal(), Program, Declare, Public, Global, Begin, Repeat, Loop, frame

This is for example when a ship is needed, of which the speed and name want to be accessible from the rest of the program. This way, one can easily have multiple instances of the same ProcessType, but still have the appropriate variables easily accessible.

Notice the use of Declare. If we wouldn't use it, we could just move the process SpaceShip above the main process. This will have the same result.
