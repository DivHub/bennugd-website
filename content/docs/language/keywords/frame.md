---
title: frame
---

    Frame [ ( <percentage> ) ] ; 

The `frame;` command tells the interpreter when a [process]({{< ref "docs/language/keywords/process" >}}) is done for one game cycle. When the `frame;` is reached, the screen is updated. If there are several processes running, the screen is updated once every process has reached its `frame;` statement.

It is commonly used in [loops]({{< ref "loops" >}}) of processes that should do something like moving around by a certain amount of pixels per game cycle (or per frame).

A possibility is to adjust the amount of cycles to wait. `frame(100);` would wait one cycle (100%), same as `frame;`. However `frame(200);` will wait two cycles (200% means the frame statement provides for 200% frame). So `frame(50);` will wait a half cycle or otherwise said, it will make a loop run twice per frame. 

## Example

```
Process Main()
Begin

    square();

    Repeat
        frame;
    Until(key(_ESC))

    exit();

End

Process square()
Begin

    graph = new_map(5,5,16);
    map_clear(0,graph,rgb(255,255,255));

    Loop
        x += 2 * (key(_right)-key(_left));
        frame; //<-vital part
    End

End
```