---
title: Pointer
---

## Syntax

Declaration of a pointer:

```
<datatype> POINTER <pointername>
<datatype> * <pointername>
```

Assignment of a value to the location pointed to:

```
POINTER <pointername> = <value>;
* <pointername> = <value>;
```

| Notation | Description |
|---|---|
| `< ... >` | item |
| `[ ... ]` | optional |
| `( ... )*` | 0 or more times |
| `( ... )+` | 1 or more times |
{.table}

## Description

Pointers, are used to point to a location in memory. It uses 32 bits (4 bytes) so it can map 4GB of memory into bytes.

Pointers can point to any datatype: ints, shorts, strings or even usermade datatypes. However, using a `struct pointer my_pointer` is pointless, because the compiler has no knowledge of the elements inside the struct pointing to, since it doesn't know which struct is meant, so this is invalid.

`MyStruct pointer my_pointer`, where `MyStruct` is an existing struct, is also not valid, because `MyStruct` is not a datatype. The only way to have something like a `struct pointer my_pointer` is to use `Type` as seen in the example.

## Example

```
import "mod_say"

Type _point
    int x;
    int y;
End

Type _person
    string name;
    int age;
End

Global
    _person Person;
End

Process Main()
Private
    int my_int;
    int* my_int_pointer;
    _point myPoint;
    _person* personPointer; // possible, because _person is infact a datatype
    //Person* personPointer; // not possible, because Person is not a datatype
Begin

    my_int_pointer = &my_int;

    my_int = 3;
    say(my_int);
    say(*my_int_pointer);

    *my_int_pointer = 4;
    say(my_int);
    say(*my_int_pointer);

    setXY(&myPoint);
    say(myPoint.x);
    say(myPoint.y);

    personPointer = &Person;
    personPointer.name = "Mies";
    say(Person.name);
    say(personPointer.name);

End

Function int setXY(_point* p)
Begin
    p.x = 3; // this is actually (*p).x = 3, but . can be used like this
    p.y = 5; // this is actually (*p).y = 5, but . can be used like this
    return 0;
End
```

Used in example: say(), key(), Type, Global, Private, point

The `&` (offset) operator, when used with pointers, returns a `void` pointer to a variable. In the example it returns an int pointer to the variable `my_int`.

The `*` (pointer) operator, when used with pointers, makes it so the pointer variable is not accessed, but the variable it's pointing to. In the example it changes access from `my_int_pointer` to `my_int`.
