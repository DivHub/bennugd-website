---
modules:
- mod_mem
title: calloc()
---

## Definition

    VOID POINTER calloc (<INT num> ,<INT size>)

Allocates (creates) a block of memory of a certain size. Calloc is slightly different from [`alloc()`]({{< ref "/docs/language/functions/alloc" >}}), as it is more natively suited for creating arrays.

It also automatically initialises the data with zeros, so that the use of [`memset()`]({{< ref "/docs/language/functions/memset" >}}) or [`memseti()`]({{< ref "/docs/language/functions/memseti" >}}) can be omitted. Returns a pointer to the newly allocating memory block, or [NULL]({{< ref "/docs/language/constants/null" >}}) on failure.

Also called `mem_calloc()`.

## Parameters

- INT num - The amount of elements to be created in ints.
- INT size - The size of the to be allocated memory in bytes.

## Returns

VOID POINTER : Pointer to the first element of the allocated memory block.

- `NULL`    - There was are an error allocating the memory, like insufficient memory available.
- `!NULL`  - Pointer to the first element of the allocated memory block.

## Example

```
// Some general remarks with manual memory managment, ALWAYS free data after use, and test if an
// allocation was successfull with IF (p_array==NULL). When one of these memory allocation
// functions returns a NULL, the allocation was NOT sucessfull, and any kind of unpredicatable things
// can happen. With manual memory managment, you'll have to really know what you're doing, as the slightest
// mistake can cause crashes and unpredicatable behaviour, wich is one of the dangers with using pointers.

// import modules
IMPORT "mod_say";
IMPORT "mod_debug";
IMPORT "mod_mem";

/*
    calloc(int size,type);
    returns: void pointer
    purpose: create a block of memory, of a certain size, the returned pointer indicates the start adress of this block.
*/

GLOBAL

int pointer p_array;        // 10 elments, created with calloc()
int elements=10;            // initial array size
int count;                  // general purpose loop counter

PROCESS main();

BEGIN

    // Now let's use calloc to create an array, but calloc is a bit smarter then alloc. It's more suited to array's and
    // it even initializes all the data to 0 for you, so that you can omit the memset() function. In this case I
    // kept memseti() in there, but you can omit it when using calloc(). But with alloc() you need to use it!

    // Note the small difference between alloc() and calloc().

    //p_array=alloc(elements*sizeof(int));
    p_array=calloc(elements,sizeof(int));   // 10 * 4 bytes (the size of an int)


    // check if the allocation succeeded
    IF (p_array==NULL)
       // allocation failed
       say("allocation failed!! p_array="+p_array);

    ELSE

       // allocation succeeded
       // set the value's to zero
       /*
       memseti(p_array ,0,elements); // not need for calloc();
       */

       say("");
       say("");
       // print the array
       FOR (count=0; count<elements; count+=1)
           say("p_array["+count+"]="+p_array[count]);
       END

       say("");
       say("");
       say("the size of the array is "+(elements*sizeof(int))+" bytes");
       say("");
       say("");
    END

ONEXIT

   // Free the used memory
   say("freeing old memory........");

   say("p_array...");
   free(p_array);
   say("ok");

END
```

Used in example: alloc(), memset(), memsetw(), memseti(), sizeof(), say(), free(), OnExit, pointer, sizeof
