---
modules:
- internals
title: Process statuscodes
---

Process statuscodes are status codes used for the local variable `Reserved.status`, to specify the current status of a process.

## List

| Constant | Value | Description |
|---|---|---|
| `STATUS_DEAD` | 0 | The process is dead. |
| `STATUS_KILLED` | 1 | The process is killed. |
| `STATUS_RUNNING` | 2 | The process is running. |
| `STATUS_SLEEPING` | 3 | The process is sleeping. |
| `STATUS_FROZEN` | 4 | The process is frozen. |
| `STATUS_WAITING` | 7 | The process is waiting.  |
{.table}
