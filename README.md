# SmartTrash – Intelligent Waste Bin System

This project offers a complete intelligent waste management solution, composed of three main parts:  
- **[Embedded Electronics (ESP32)](https://github.com/boujnan03/SmartWaste-Management/tree/main/smartTrash_arduino)**
- **[Server/API (FastAPI + MongoDB + Firebase RTDB)](https://github.com/boujnan03/SmartWaste-Management/tree/main/smartTrash_API)**
- **[Mobile Application (Flutter)](https://github.com/boujnan03/SmartWaste-Management/tree/main/smartTrash_flutter/smart_trash)**

It allows real-time measurement and monitoring of fill level, weight, humidity, temperature, water presence, and gas in the trash bin, with local display and data transmission to a user interface.

---

## 1. Electronics Part (ESP32)

### Main Features
- Fill level measurement (ultrasonic)
- Weight measurement (HX711)
- Temperature and humidity (DHT11)
- Gas detection (MQ-2 or similar)
- Water detection (analog sensor)
- Automatic lid opening (servo)
- Sound alert (buzzer)
- Local display (I2C LCD)
- Periodic data transmission to server via WiFi

### Connection Diagram (example)
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

### Arduino Dependencies
- WiFi
- HTTPClient
- Wire
- DHT sensor library
- LiquidCrystal_I2C
- ESP32Servo
- HX711

### Main File:  
`smartTrash_arduino/sketch_smartTrash.ino`

---

## 2. Server / API Part (FastAPI + MongoDB + Firebase RTDB)

### Main Features
- Reception of data sent by ESP32 (POST JSON)
- Data storage in MongoDB (history, statistics)
- Real-time synchronization with Firebase Realtime Database (for Flutter application)
- REST API provision for the application (consultation, statistics, alerts)
- Authentication (optional)
- Multi-bin management (optional)

### Technologies Used
- **Backend:** Python [FastAPI](https://fastapi.tiangolo.com/)
- **Database:** [MongoDB](https://www.mongodb.com/)
- **Real-time:** [Firebase Realtime Database](https://firebase.google.com/products/realtime-database)

### API Endpoint Example
```
POST /update/trash_1
Content-Type: application/json
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

### Main Files:  
- `smartTrash_API/main.py` (FastAPI)
- `smartTrash_API/requirements.txt`
- MongoDB and Firebase configuration in the `smartTrash_API/` folder

---

## 3. Mobile Application Part (Flutter)

### Main Features
- Real-time visualization of each bin's data (via Firebase RTDB)
- Location mapping
- Alerts (full bin, water leak, gas detected...)
- Statistics and history
- User authentication (optional)

### Technologies Used
- [Flutter](https://flutter.dev/)
- [Firebase RTDB](https://firebase.google.com/products/realtime-database)
- For mapping:
  - [flutter_osm_plugin (OpenStreetMap)](https://pub.dev/packages/flutter_osm_plugin) **(open source, recommended)**
  - or [Google Maps Flutter](https://pub.dev/packages/google_maps_flutter)
- [Provider](https://pub.dev/packages/provider) or [Bloc](https://bloclibrary.dev/) for state management

### Main Files:  
- `smartTrash_flutter/smart_trash/` (Flutter application folder)
- `smartTrash_flutter/smart_trash/lib/` (Dart sources)

---

## Installation and Launch

### 1. Electronics Part
- Program the ESP32 with the Arduino code
- Adapt the WiFi SSID/password and server URL in the code
- Connect the sensors according to the diagram

### 2. Server Part
- Install Python dependencies:  
  ```bash
  cd server
  pip install -r requirements.txt
  ```
- Launch the server:  
  ```bash
  uvicorn main:app --reload
  ```
- Ensure MongoDB and Firebase are configured and accessible

### 3. Flutter Application Part
- Install Flutter: [Official Guide](https://docs.flutter.dev/get-started/install)
- Install dependencies:  
  ```bash
  cd app
  flutter pub get
  ```
- Launch the application:  
  ```bash
  flutter run
  ```

---

## Architecture Diagram

```
[ESP32 + Sensors]  <---WiFi--->  [FastAPI Server]  <---MongoDB/Firebase--->  [Flutter Application]
```

> **Important:** The ESP32 and API server must be connected to the same WiFi network (same router) for communication to work properly.

---

## Authors

Project developed by:
- [Yassine Boujnan](https://github.com/boujnan03)
- [WAM](https://github.com/walid-moussa55)
- [Momoun Ouhda](https://github.com/mimounouhd)
- [Mohamed Belghiti Alaoui]()
- [Meryem Echbab]()
- [Bouchra Manoussi]()
- [Raja Benaddi]()
---

## Useful Links

- [Official ESP32 Documentation (Espressif)](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [MongoDB](https://www.mongodb.com/)
- [Firebase RTDB](https://firebase.google.com/products/realtime-database)
- [Flutter](https://flutter.dev/)
- [Google Maps Flutter](https://pub.dev/packages/google_maps_flutter)
- [Arduino France Forum](https://forum.arduino.cc/c/international/francais/33)
- [Arduino HTTPClient Request Examples](https://randomnerdtutorials.com/esp32-http-get-post-arduino/)
- [SmartTrash Project Repository](https://github.com/boujnan03/SmartWaste-Management/)

---

**SmartTrash**: Optimize urban waste management through data and artificial intelligence!

---