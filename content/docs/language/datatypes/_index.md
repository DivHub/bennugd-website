---
title: Data Types
---

Datatypes give meaning to data and dictate how a variable acts and reacts. Examples of datatypes are ints, floats and strings. Special cases are voids, arrays, varspaces and structs. User made types can also be defined, by use of the operator Type.

## List of Types

- [`Array`]({{< ref "array" >}})
- Byte
- Float
- Int
- [`Pointer`]({{< ref "pointer" >}})
- Short
- [`sizeof()`]({{< ref "sizeof" >}})
- [`String`]({{< ref "string" >}})
- [`Struct`]({{< ref "struct" >}})
- Varspace
- Void
- Word

## Byte

    BYTE

Bytes are whole numbers ranging from 0 to 2^8-1 ( 0 to 255 ). This is because a byte uses 8 bits (1 byte) to denote its value. A byte is the smallest datatype directly accessible in nowadays memory.

## Float

    FLOAT

Floats are floating point numbers ranging from about -10^38.53 to about 10^38.53. This is achieved by dividing 32 bits (4 bytes) in a certain way, with a certain precision. A float is used for operations in which both very large and small numbers are used, while rounding is not permitted. Unlike ints or shorts, a float actually has decimal digits. Their accuracy is about 7 decimal digits.

## Int

    INT

Ints (short for integer, meaning wholes), are whole numbers ranging from -2^31 to 2^31-1 ( -2147483648 to 2147483647 ). This is because an integer uses 32bits (4 bytes) to denote its value using the Two's complement system.

## Short / Word

    SHORT or WORD

Shorts or Words are whole numbers ranging from 0 to 2^16-1 ( 0 to 65535 ). This is because a short or word uses 16 bits (2 bytes) to denote its value.

## Varspace

    VARSPACE

A varspace is a datatype of any datatype. When a function, like sort() or fread(), has a parameter of type varspace, it means it needs a variable of any type.

## Void

    VOID

Bennu doesn't have voids as such. But when we look at for example the function free(), we see that you can pass it a void pointer. This means, that you can pass it a pointer of whatever type you want; an int pointer, word pointer or even a pointer pointer. So in this case, void means "undefined".

There is another case in which voids can occur. This is when a function returns nothing, but this never happens in Bennu.

## Example

```
import "mod_draw"
import "mod_wm"
import "mod_key"
import "mod_map"

Type _point
    int x;
    int y;
End

Process Main()
Private
    _point A,B;
Begin

    // Init the points
    A.x = 100;
    A.y = 50;
    B.x = 250;
    B.y = 150;

    // Setup drawing
    drawing_map(0,0);
    drawing_color(rgb(0,255,255));

    // Draw a box
    drw_box(A,B);

    // Wait for key ESC or X button
    Repeat
        frame;
    Until(key(_ESC)||exit_status)

End

// Draw a box using two points
Function int drw_box(_point A, _point B)
Begin
    return draw_box(A.x,A.y,B.x,B.y);
End
```

Used in example: drawing_map(), drawing_color(), rgb(), key(), draw_box(), exit_status
