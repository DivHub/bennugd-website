---
title: Bit Flags
---

Bit flags are constants which each denotes a single unique case in one situation and can be combined to form different, unique cases.

They are called *bit flags*, because when bits are used to denote a cases, we observe they are indeed single and unique and can be combined to form different unique combinations.

Bit flags are often used as integers:

| Bit pattern | Integer Value |
|---|---|
| 0001 | 1 |
| 0010 | 2 |
| 0100 | 4 |
| 1000 | 8 |
{.table}

These can be combined to form, for example:

| Bit pattern | Integer Value |
|---|---|
| 1000 | 9 |
| 0110 | 6 |
| 1110 | 14 |
| 0101 | 5 |
{.table}

## Example

When we look at [Blit Flags]({{< ref "/docs/language/constants/blit_flags" >}}) for example, we see the values:

| Constant | Value
|---|---|
| `B_HMIRROR` | 1 |
| `B_VMIRROR` | 2 |
| `B_TRANSLUCENT` | 4 |
| `B_ALPHA` | 8 |
| `B_ABLEND` | 16 |
| `B_SBLEND` | 32 |
| `B_NOCOLORKEY` | 128 |
{.table}

These are all single unique cases and can be combined to form different unique cases. For example, when we want a translucent, horizontally mirrored blit operation with use of additive blending, we would do:

```
B_HMIRROR | B_TRANSLUCENT | B_ABLEND
1         | 4             | 16       = 21
```

Because the bits are unique, the addition operator can also be used. But when we consider there would be a constant called `B_HVMIRROR`, which has the value `B_HMIRROR|B_VMIRROR` (3), the addition operator can't be used all the time:

```
B_HMIRROR | B_HVMIRROR == 1 | 3 == 3
B_HMIRROR + B_HVMIRROR == 1 + 3 == 4
```

In conclusion, use the bor operator when dealing with bit flags to be on the safe side.

## Usage Example

```
Process main()
Private
    unsigned byte options;
Begin

    /* Manipulate bit flags */

    // To set options, use = (the bits with 1's will be targeted)
    options = 01000001b;

    // To add options, use | (the bits with 1's will be targeted)
    options |= 00000001b;

    // To remove options, use & and ~ (the bits with 1's will be targeted)
    options &= ~00010000b;
    // same: options &= 11101111h (the bits with 0's will be targeted)

    // To switch options, use ^ (the bits with 1's will be targeted)
    options ^= 10000000b;

    /* Manipulate bit flags using the << operator (these are equivalent to the last three) */

    options|= 1<<0; // position 0 is now ON
    options&= ~(1<<4); // position 4 is now OFF
    options^= (1<<7); // position 7 is now SWITCHED

    /* Checking of bit flags */

    // Check if a certain option is set (the bits with 1's will be checked)
    if((options&10000000b)==10000000b)
    end

    // Check if a certain option is not set (the bits with 1's will be checked)
    if((options&10000000b)==0)
    end

    // Check if multiple options are set (the bits with 1's will be checked)
    if((options&10000001b)==10000001b)
    end

    // Check if multiple options are not set (the bits with 1's will be checked)
    if((options&00000110b)==0)
    end

    // Check if at least one of multiple options is set (the bits with 1's will be checked)
    if((options&00000110b)!=0)
    end

    // Check if at least one of multiple options is not set (the bits with 1's will be checked)
    if((options&00000110b)!=00000110b)
    end

    /* Checking of bit flags using the << operator */

    // Check if a certain option is set
    if((options&(1<<7))==(1<<7)) // position 7 is ON
    end

    // Check if a certain option is not set
    if((options&(1<<7))==0) // position 7 is OFF
    end

End
```

Used in example: Bitwise Operators.
