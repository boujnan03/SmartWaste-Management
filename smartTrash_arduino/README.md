# SmartTrash Arduino

This project controls a smart trash bin using an ESP32, sensors, and an LCD display. It measures fill level, weight, humidity, temperature, water level, and gas, then sends this data to a server via WiFi.

## Hardware Used

- ESP32
- 2 x HC-SR04 ultrasonic sensors (object detection and trash bin level)
- DHT11 sensor (temperature and humidity)
- Gas sensor (MQ-2 or similar)
- Water sensor
- HX711 module + load cell (weight)
- Servo motor (lid opening)
- Buzzer
- 16x2 I2C LCD display

## Features

- Measures trash bin fill level
- Measures waste weight
- Detects humidity and temperature
- Gas detection
- Water level detection (buzzer alert if too high)
- Automatic lid opening when an object is detected
- Information display on LCD screen
- Periodic data transmission to server via HTTP POST

## Hardware Connections

| Sensor/Module       | ESP32 Pin   |
|---------------------|-------------|
| TRIG_OBJ            | 4           |
| ECHO_OBJ            | 5           |
| TRIG_TRASH          | 19          |
| ECHO_TRASH          | 18          |
| DHT11               | 23          |
| Water sensor        | 32          |
| Gas sensor          | 34 (A0)     |
| HX711_DT            | 26          |
| HX711_SCK           | 27          |
| Servo               | 25          |
| Buzzer              | 33          |
| I2C LCD             | SDA: 21, SCL: 22 |

## WiFi Configuration

> **Important:** The ESP32 and API server must be connected to the same WiFi network (same router) for communication to work properly.

Modify the following lines in the code to adapt the WiFi SSID and password:

```cpp
#define WIFI_SSID ""
#define WIFI_PASSWORD ""
```

## Server Configuration

Modify the server URL to point to your API:

```cpp
const char* serverName = "http://API_SERVER_IPADDRESS:8000/update/trash_1";
```

## Usage

1. Upload the code [sketch_smartTrash.ino](smartTrash_arduino/sketch_smartTrash.ino) to your ESP32.
2. Connect all sensors/modules according to the table above.
3. Open the serial monitor at 115200 baud to see the logs.
4. Data will be automatically sent to the server every 10 seconds.

## Arduino Dependencies

Install the following libraries via the Arduino Library Manager:

- WiFi
- HTTPClient
- Wire
- DHT sensor library
- LiquidCrystal_I2C
- ESP32Servo
- HX711

## Example JSON Frame Sent

```json
{
  "bin_id": "trash_1",
  "gaz_level": 5,
  "humidity": 45.2,
  "temperature": 23.1,
  "location": {"latitude": 32.376553, "longitude": -6.320284},
  "name": "Bin 1 - Lobby",
  "trash_level": 80,
  "trash_type": "plastic",
  "weight": 2.5,
  "volume": 100,
  "water_level": 60
}
```

## Useful Links

- [Official ESP32 Documentation (Espressif)](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)
- [Arduino HX711 Library](https://github.com/bogde/HX711)
- [Arduino DHT sensor Library](https://github.com/adafruit/DHT-sensor-library)
- [LiquidCrystal_I2C Library](https://github.com/johnrickman/LiquidCrystal_I2C)
- [ESP32Servo Library](https://github.com/jkb-git/ESP32Servo)
- [Arduino HTTPClient Request Examples](https://randomnerdtutorials.com/esp32-http-get-post-arduino/)
