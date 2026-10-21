# Wiring

## Connections

| MPU6050 (GY-521) | ESP32 Dev Module |
|------------------|------------------|
| VCC              | 3V3              |
| GND              | GND              |
| SDA              | GPIO 21          |
| SCL              | GPIO 22          |
| AD0              | GND (I2C address 0x68) |
| INT, XDA, XCL    | not connected    |

## Diagram

```
   MPU6050                 ESP32 Dev Module
  +--------+              +----------------+
  |  VCC   |--------------| 3V3            |
  |  GND   |--------------| GND            |
  |  SDA   |--------------| GPIO 21        |
  |  SCL   |--------------| GPIO 22        |
  |  AD0   |--------------| GND            |
  +--------+              +----------------+
```

## Notes

- Power the MPU6050 from **3V3**, not 5V, unless your breakout has a regulator and you know it does.
- Keep the wires short and solid. Loose I2C wires cause random freezes.
- Mount the board flat with the chip facing up. Gestures assume this orientation. If you mount it differently, use `SWAP_AXES` and the `INVERT_*` options.
- For wireless use, power the ESP32 from a LiPo through a TP4056 charger module, or a USB power bank.

## Orientation

```
        up/down tilt (pitch)
              ^
              |
  left/right -+--> roll flick = click
  rotate (yaw)
```
