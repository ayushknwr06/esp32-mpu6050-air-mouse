# Tuning guide

All values are at the top of `AirMouse/AirMouse.ino`. Re-upload after each change.

## Cursor

| Setting | Default | Effect |
|---|---|---|
| `SENSITIVITY` | 0.25 | Higher is faster. Try 0.1 to 0.6. |
| `DEADZONE` | 1.0 | Gyro rate (deg/s) ignored. Raise to 1.5 or 2 if the cursor drifts. |
| `SWAP_AXES` | false | Swap X and Y if the board is mounted on its edge. |
| `INVERT_X`, `INVERT_Y` | false | Flip a cursor direction. |

## Clicks

| Setting | Default | Effect |
|---|---|---|
| `CLICK_THRESH` | 130 | Roll speed (deg/s) needed to click. Raise to 180 to 250 for fewer accidental clicks, lower to 90 to 110 if clicks don't register. |
| `CLICK_LOCKOUT` | 300 | Minimum ms between clicks. |
| `WOBBLE_FREEZE` | 50 | Roll rate that freezes the cursor so a flick doesn't move it. |
| `FREEZE_AFTER` | 250 | ms the cursor stays frozen after a click. |
| `INVERT_CLICKS` | false | Swap left and right click directions. |

Flick out, then ease back slowly. A fast return flick is blocked by the lockout.

## Scrolling

| Setting | Default | Effect |
|---|---|---|
| `SCROLL_ENTER` | 0.70 | Side tilt needed to enter scroll mode (0.7 is about 45 degrees). Raise to 0.8 if it triggers by accident, lower to 0.6 if hard to enter. |
| `SCROLL_EXIT` | 0.50 | Side tilt below which scroll mode ends. |
| `SCROLL_DEAD` | 0.15 | Forward/back tilt ignored near level. Raise to 0.25 if scrolling creeps. |
| `SCROLL_SPEED` | 25 | Notches per second at full tilt. Try 10 to 50. |
| `INVERT_SCROLL` | false | Reverse scroll direction. |

Roll into scroll mode slowly so it isn't read as a click flick.

## Calibration

The gyro offset is measured at startup for about 2 seconds. Keep the board still on a table until the Serial Monitor prints "Done." Press the EN/RST button to recalibrate.
