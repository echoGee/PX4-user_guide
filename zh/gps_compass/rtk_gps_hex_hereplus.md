# HEX/ProfiCNC Here+ RTK GPS

The [Here+ RTK GPS receiver](http://www.proficnc.com/content/12-here) is a small, light and energy efficient [RTK GPS module](../gps_compass/rtk_gps.md), based on the u-blox M8P. 使用RTK，PX4控制器可以获取到它的位置，并且这个位置的精度可以达到厘米级的精度，这比普通GPS提供的位置更加精确。

![](../../assets/hardware/gps/rtk_here_plus.jpg)

## 购买

* [ProfiCNC](http://www.proficnc.com/gps/77-gps-module.html)
* [Hex - China](http://www.hex.aero/shop/all/here-rtk-gnss-set/) (China)
* [Other resellers](http://www.proficnc.com/stores)

## 配置

RTK setup and use on PX4 via *QGroundControl* is largely plug and play (see [RTK GPS](../advanced_features/rtk-gps.md) for more information).

## 针脚定义

The Here+ GPS comes with an 8 pin connector with the following pinout

![Here+ Pinout (viewed from base)](../../assets/hardware/gps/rtk_here_plus_connectors.jpg)

| 针脚         | Here+ GPS     |
| ---------- | ------------- |
| 1 (purple) | VCC_5V        |
| 2 (blue)   | GPS_RX        |
| 3 (green)  | GPS_TX        |
| 4 (yellow) | I2C SCL       |
| 5 (orange) | I2C SDA       |
| 6（红）       | SAFETY BUTTON |
| 7 (brown)  | BUTTON_LED    |
| 8 (black)  | GND           |

## 接线和连接

Connection examples are shown below for a number of boards (these can be used to modify the cable as needed for other boards).

### Hex Cube

The supplied cable can be inserted directly into the [Hex Cube (Pixhawk 2)](../flight_controller/pixhawk-2.md) GPS UART port.

#### Pixhawk 3 Pro

The [Pixhawk 3 Pro](../flight_controller/pixhawk3_pro.md) and [Pixracer](../flight_controller/pixracer.md) have a 6 pin GPS port connector. For these controllers you can modify the GPS cable (as shown below) to remove pin 6 and 7.

![rtk_here_plug_gps_to_6pin_connector](../../assets/hardware/gps/rtk_here_plug_gps_to_6pin_connector.jpg)

Pin 6 and 7 are for the safety button - these can be attached as well if needed.

| 针脚 | Here+ GPS  | 针脚 | Pixhawk 3 Pro GPS |
| -- | ---------- | -- | ----------------- |
| 1  | VCC_5V     | 1  | VCC               |
| 2  | GPS_RX     | 2  | GPS_TX            |
| 3  | GPS_TX     | 3  | GPS_RX            |
| 4  | I2C SCL    | 4  | SCL               |
| 5  | I2C SDA    | 5  | SDA               |
| 6  | BUTTON     | -  | -                 |
| 7  | BUTTON_LED | -  | -                 |
| 8  | GND        | 6  | GND               |

#### Pixhawk 4

The Here+ to [Pixhawk 4](../flight_controller/pixhawk4.md) GPS port pin mapping is 1:1 for pins 1-7 and then connect GND (Here+ pin 8 / Pixhawk pin 10). Pixhawk 4 GPS port pins 8 and 9 can be left disconnected.

:::note
The Pixhawk 4 GPS port has pin 1 on the left hand side.
:::

| 针脚 | Here+ GPS  | 引脚 | Pixhawk 4 GPS Port  |
| -- | ---------- | -- | ------------------- |
| 1  | VCC_5V     | 1  | VCC (+5V)           |
| 2  | GPS_RX     | 2  | GPS_TX              |
| 3  | GPS_TX     | 3  | GPS_RX              |
| 4  | I2C SCL    | 4  | SCL1                |
| 5  | I2C SDA    | 5  | SDA1                |
| 6  | BUTTON     | 6  | SAFETY_SWITCH       |
| 7  | BUTTON_LED | 7  | SAFETY_SWITCH_LED |
| /  | -          | 8  | VDD_3V3             |
| /  | -          | 9  | BUZZER              |
| 8  | GND        | 10 | GND                 |