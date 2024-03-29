---
modules:
- mod_cd
title: CD Status Codes
---

CD statuscodes are status codes returned by the function [`cd_status()`]({{< ref "/docs/language/functions/cd_status" >}}), to specify the current status of a CD drive.

## List

| Constant | Value | Description |
|---|---|---|
| `CD_ERROR` | -1 | Error. |
| `CD_TRAYEMPTY` | 0 | The CD tray is empty. |
| `CD_STOPPED` | 1 | The CD is stopped. |
| `CD_PLAYING` | 2 | The CD is playing. |
| `CD_PAUSED` | 3 | The CD is paused. |
{.table}
