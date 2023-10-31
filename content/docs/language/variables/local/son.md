---
title: son
---

    INT son

Son is a predefined [local variable]({{< ref "/docs/language/variables/local/" >}}). Son holds the ProcessID of the process/function that was last called by the current process/function

There are several other local variables which refer to the ProcessID of a related process:

- Father
- Bigbro
- Smallbro

## Example

```
Program example;
Begin
    first_process();
    Loop
        frame;
    End
End

Process first_process()  // Declaration of the first process
Begin
    second_process();  // Call the second process
    Loop
        frame; // This loop makes "first_process()" a process rather than a function
    End
End

Process second_process()  //declaration of another process
Begin
    x = father.x; // These two lines use the father variable to move this process
    y = father.y; // to the position of first_process, as the father variable here
                  // holds the ProcessID of "first_process()"
    Loop
        frame;
    End
End
```
