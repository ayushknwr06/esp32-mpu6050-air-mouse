# ESP32 MPU6050 Air Mouse

A gesture-only Bluetooth air mouse. An ESP32 and an MPU6050 gyro turn hand motion into cursor movement, clicks, and scrolling on your laptop. No buttons needed.

## Features

- Cursor control by rotating and tilting the board
- Left and right click by a quick roll flick
- Scroll mode by rolling the board onto its side
- Pause by flipping the board upside down
- Gyro calibration at startup and tunable sensitivity

## Hardware

- ESP32 Dev Module
- MPU6050 (GY-521)
- Jumper wires, and optionally a LiPo battery with a TP4056 charger

## Wiring

| MPU6050 | ESP32   |
|---------|---------|
| VCC     | 3V3     |
| GND     | GND     |
| SDA     | GPIO 21 |
| SCL     | GPIO 22 |
| AD0     | GND     |

## Gestures

| Gesture | Action |
|---|---|
| Rotate left/right | Cursor left/right |
| Tilt up/down | Cursor up/down |
| Quick roll flick right | Left click |
| Quick roll flick left | Right click |
| Roll board onto its side (~45°+) | Scroll mode, tilt to scroll |
| Roll back flat | Back to cursor |
| Flip upside down | Pause |

## Setup

1. Install Arduino IDE and the ESP32 board package.
2. Install the [ESP32-BLE-Mouse](https://github.com/T-vK/ESP32-BLE-Mouse) library (Sketch, Include Library, Add .ZIP Library).
3. Select **ESP32 Dev Module** and upload `AirMouse/AirMouse.ino`.
4. Keep the board still for about 2 seconds while it calibrates (Serial Monitor at 115200 shows "Done.").
5. Pair **ESP32 Air Mouse** in your laptop's Bluetooth settings.

### Compile errors with ESP32 core 3.x

The T-vK library was written for core 2.x. Either use ESP32 core **2.0.17**, or patch two lines in `BleMouse.cpp`:

```cpp
BLEDevice::init(String(bleMouseInstance->deviceName.c_str()));
bleMouseInstance->hid->manufacturer()->setValue(String(bleMouseInstance->deviceManufacturer.c_str()));
```

## Tuning

Edit the values at the top of the sketch:

| Setting | Purpose |
|---|---|
| `SENSITIVITY` | Cursor speed (0.1 to 0.6) |
| `DEADZONE` | Ignore small drift (1.0 to 2.0) |
| `CLICK_THRESH` | Flick strength needed to click |
| `SCROLL_SPEED`, `SCROLL_ENTER` | Scroll speed and when scroll mode starts |
| `INVERT_X`, `INVERT_Y`, `INVERT_CLICKS`, `INVERT_SCROLL`, `SWAP_AXES` | Fix wrong directions |

## Troubleshooting

- **No cursor movement:** check SDA/SCL wiring and that Serial shows "Done."
- **Drift:** keep the board still at power-up and raise `DEADZONE`.
- **Won't pair:** remove the old "ESP32 Air Mouse" entry from Bluetooth settings and pair again.

## License
![Wiring photo](esp32-mpu6050-air-mouse
/Screenshot 2026-10-21 195226.png)

MIT
