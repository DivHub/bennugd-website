---
modules:
- mod_rand
title: rand_seed()
---

## Definition

    INT rand_seed ( <INT seed> )

Seeds the random generator, used in `rand()`.

This is useful for synchronizing the random generator on multiple machines, as when the same seed is used, calls to `rand()` with the same limits will return values in the same order on all the machines.

To reset the seeding to its original state, meaning the state before any call to `rand()` or `rand_seed()`, set seed to 1.

## Parameters

- INT seed  - The seed for the random generator used in `rand()`; 1 to reset.

## Returns

INT: true

## Example

```
import "mod_rand"
import "mod_say"
import "mod_time"

Process Main()
Begin
  say("First number: " + (rand(0,1000)%100));
  rand_seed(time());
  say("Random number: " + (rand(0,1000)%100));
  rand_seed(1);
  say("Again the first number: " + (rand(0,1000)%100));
End
```

Used in example: `say()`, `rand()`, `rand_seed()`
