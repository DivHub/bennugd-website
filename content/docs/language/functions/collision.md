---
modules:
- mod_grproc
title: collision()
---

## Definition

    INT collision ( <INT processID|processTypeID> )

Checks if a process collided with the process calling `collision()`.

When a `processTypeID` is specified, there could be multiple fitting collisions. In this case, `collision()` returns a `processID` on each subsequent call, until it returns `0`. This can be reset by use of the `frame;` statement, and in such case, `frame(0);` can be handy.

See also [`collision_box()`]({{< ref "/docs/language/functions/collision_box" >}}) and [`collision_circle()`]({{< ref "/docs/language/functions/collision_circle" >}}).

## Parameters

- INT processID|processTypeID - The ProcessID of the process or the ProcessTypeID of the type of processes to be checked.

## Returns

INT : The ID of the collided process.

- `0 ` - No collision
- `>0` - The processID of the process colliding with the current process

## Example

```
Process SpaceShip( int file , int graph , int x , int y , int angle , int maxspeed , int maxturnspeed )
Private
    int speed;
    int collisionID;
    string text;
Begin
    write_string(0,0,0,0,&text);
    Loop
        // Handle movement
        speed+=key(_up)*(speed<maxspeed)-key(_down)*(speed>-maxspeed);
        angle+=(key(_left)-key(_right))*maxturnspeed;
        advance(speed);
        // Handle collision
        if( (collisionID = collision(type main)))
            text = "collision with: " + collisionID;
        else
            text = "no collision";
        end
        frame;
    End
End

Process Main()
Private
    int map;
Begin

    // Create the graph for the ship
    map = map_new(20,20,8);
    map_clear(0,map,rgb(0,255,255));

    // Create the graph for the Main process
    graph = map_new(50,50,8);
    map_clear(0,graph,rgb(255,255,0));

    // Position the main process and create the ship
    x = y = z = 100;
    SpaceShip(0,map,100,100,0,20,5000);

    Repeat
        frame;
    Until(key(_ESC))

    let_me_alone();

End
```

Used in example: [`write_string()`]({{< ref "/docs/language/functions/write_string" >}}), [`key()`]({{< ref "/docs/language/functions/key" >}}), [`collision()`]({{< ref "/docs/language/functions/collision" >}}), [`map_new()`]({{< ref "/docs/language/functions/map_new" >}}), [`map_clear()`]({{< ref "/docs/language/functions/map_clear" >}}), [`advance()`]({{< ref "/docs/language/functions/advance" >}}), [`let_me_alone()`]({{< ref "/docs/language/functions/let_me_alone" >}}), graph, type.
