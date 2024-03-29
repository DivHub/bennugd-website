---
modules:
- mod_proc
title: let_me_alone()
---

## Definition

    INT let_me_alone ( )

Kills all [processes](#) except the calling one.

To kill only one process, use [`signal()`]({{< ref "/docs/language/functions/signal" >}}).

## Returns

INT: true

## Example

```
Const
    screen_width = 320;
    screen_height = 200;
    screen_depth = 8;
End

/**
 * Description
 *   Generates an error. Puts the error in the console and stdout.txt and shows it onscreen
 *   for certain time. Immediately kills all other processes and quits the program after a
 *   certain time.
 *
 * Parameters
 *   String message   - The error message.
 *   int delay        - The time to display the error onscreen and after which the program will quit.
 *                      In 1/100seconds.
 *
 * Returns
 *   0 - Success.
 */
Process error(String message,int delay)
Begin

    // Put the error message in the console and in stdout.txt
    say("[ERROR] " + message);

    // Show the error message onscreen, the size adjust for the screen width
    set_text_color(rgb(255,0,0));
    graph = write_in_map(0,message,4);
    size = 100*(screen_width-10)/graphic_info(0,graph,G_WIDTH);
    x = screen_width/2;
    y = screen_height/2;

    // Kill all other processes
    let_me_alone();

    // Wait the specified time
    timer[0] = 0;
    Repeat
        frame;
    Until(timer[0]>delay)

    // Unload the used graph
    unload_map(0,graph);

    return 0;

End

Process Main();
Begin

    // Set the screen mode
    set_mode(screen_width,screen_height,screen_depth);

    // Generate an error
    error("ERROR, QUITTING IN 2 SECONDS",200);

    Repeat
        frame;
    Until(key(_esc))

End
```
