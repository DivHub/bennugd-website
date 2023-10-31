---
title: Loops
---

## Loop ... End

```
Loop
    // Statements
End

```

-   The statements will be repeated indefinitely.

## While ... End

```
While(<condition>)
    // Statements
End

```

-   The statements will be repeated while _condition_ is fulfilled.

## Repeat ... Until

```
Repeat
    // Statements
Until(<condition>)

```

-   The statements will be repeated until _condition_ is fulfilled.

## For ... End

```
For( [ <initializer> ]; [ <condition> ]; [ <counting expression> ] )
    // Statements
End

```

-   First, _initializer_ will be executed. Then the statements will be repeated until _condition_ is fulfilled. After each run of the statements, _counting expression_ is executed.

## From ... End

```
From <variable>=<startvalue> To <endvalue> [ Step <incrementvalue> ];
    // Statements
End

```

-   First, _startvalue_ will be assigned to the variable. Then the statements will be repeated and _incrementvalue_ added to the variable. When the variable is greater than _endvalue_, the loop ends.
-   Note that _incrementvalue_ must be a [constant](http://wiki.bennugd.org/index.php?title=Constant "Constant"). The `Step <incrementvalue>` part is optional.

## Manipulating a loop

There are more ways to manipulate a loop, both internally and externally.

If the code inside a loop reaches a [break](http://wiki.bennugd.org/index.php?title=Break "Break"); statement, the loop is immediately ended. This is particularly useful in the Loop-End loop, because that one has no other way to end the loop and continue code beneath it.

If the code inside a loop reaches a [continue](http://wiki.bennugd.org/index.php?title=Continue "Continue"); statement, it executes the possible count- or stepping statement and then continues to the checking of the condition. So in a Repeat-Until loop, it would just skip to the Until() part.

If the loop is run in a specific [process](http://wiki.bennugd.org/index.php?title=Process "Process"), one can influence the execution of the loop, by changing the state of that process, by use of [signal](http://wiki.bennugd.org/index.php?title=Signal "Signal")() and [signals](http://wiki.bennugd.org/index.php?title=Signals "Signals").

## Example

```
import "mod_say"

Const
    startvalue     = 1;
    endvalue       = 8;
    incrementvalue = 2;
End

Process Main()
Private
    int c;
Begin

    /* Loop */

    c = startvalue;
    Loop
        say("Loop: " + c);
        c+=incrementvalue;
        if(c>endvalue)
            break;
        end
    End
    say("End Loop: " + c);

    /* While */

    c = startvalue;
    While(c<=endvalue)
        say("While: " + c);
        c+=incrementvalue;
    End
    say("End While: " + c);

    /* Repeat */

    c = startvalue;
    Repeat
        say("Repeat: " + c);
        c+=incrementvalue;
    Until(c>endvalue)
    say("End Repeat: " + c);

    /* For */

    For(c=startvalue;c<=endvalue;c+=incrementvalue)
        say("For: " + c);
    End
    say("End For: " + c);

    /* From */

    From c=startvalue To endvalue Step incrementvalue;
        say("From: " + c);
    End
    say("End From: " + c);

End

```

Used in example: [say](http://wiki.bennugd.org/index.php?title=Say "Say")(), [constants](http://wiki.bennugd.org/index.php?title=Constants "Constants"), [loop](http://wiki.bennugd.org/index.php?title=Loop "Loop"), [if](http://wiki.bennugd.org/index.php?title=If "If"), [break](http://wiki.bennugd.org/index.php?title=Break "Break"), [while](http://wiki.bennugd.org/index.php?title=While "While"), [repeat](http://wiki.bennugd.org/index.php?title=Repeat "Repeat"), [for](http://wiki.bennugd.org/index.php?title=For "For"), [from](http://wiki.bennugd.org/index.php?title=From "From")

In the example, all the loops do the same thing, illustrated by the use of the same constants. The output is:

```
Loop: 1
Loop: 3
Loop: 5
Loop: 7
End Loop: 9
While: 1
While: 3
While: 5
While: 7
End While: 9
Repeat: 1
Repeat: 3
Repeat: 5
Repeat: 7
End Repeat: 9
For: 1
For: 3
For: 5
For: 7
End For: 9
From: 1
From: 3
From: 5
From: 7
End From: 9

```
