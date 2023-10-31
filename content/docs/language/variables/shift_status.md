---
title: shift_status
---

## Definition

    INT shift_status

`shift_status` is defined in the [`mod_key` module]({{< ref "docs/language/modules/mod_key" >}}) and indicates whether a modifier key is being pressed. If more than a modifier key is pressed at the same time shift_status will return the sum.

## List

| Key | Value |
|---|---|
| Right Control   | 20 * |
| Left Control    | 36 |
| Right Alt   | 72 * |
| Left Alt    | 136 |
| NUM LOCK    | 256 |
| CAPS LOCK   | 512 |
| Right Shift | 1025 |
| Left Shift  | 1026 |
{.table}

> __Note__: At the time of the writing of this article, right alt and right control didn't return anything. It is unknown whether it is a bug or just deprecated.
