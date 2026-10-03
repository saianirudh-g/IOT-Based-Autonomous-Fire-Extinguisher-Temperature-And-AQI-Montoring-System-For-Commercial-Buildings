# 🔥 IOT-Based Autonomous Fire Extinguisher, Temperature and AQI Monitoring System for Commercial Buildings

## 📌 Overview

The **IoT-Based Autonomous Fire Extinguisher, Temperature and AQI Monitoring System for Commercial Buildings** is an Internet of Things (IoT) based safety and environmental monitoring system designed for multi-storey commercial buildings.

The system continuously monitors environmental parameters such as:

- 🌡️ Temperature
- 💧 Humidity
- 💨 Air-quality / gas conditions
- 🔥 Smoke and combustible gas presence

An **ESP32 microcontroller** collects information from the connected sensors and displays the measured values locally using an LCD display.

The monitored information can also be transmitted through the ESP32's Wi-Fi capability to a web-based dashboard. This allows building management or control-room personnel to observe conditions from a remote location.

When the measured temperature exceeds a predefined threshold indicating a possible fire condition, the system is designed to automatically activate the fire-extinguishing mechanism.

---

# 🎯 Project Objective

The primary objective of this project is to develop an intelligent and automated fire-safety system capable of:

1. Continuously monitoring temperature and humidity.
2. Detecting smoke and combustible gases.
3. Monitoring environmental air-quality related parameters.
4. Displaying sensor readings locally.
5. Sending sensor information to a web-based monitoring dashboard.
6. Monitoring multiple locations inside a commercial building.
7. Detecting abnormal temperature conditions.
8. Automatically activating a fire-extinguishing system when a fire condition is detected.
9. Providing remote monitoring capabilities using IoT technology.

---

# ✨ Key Features

## 🌡️ Temperature Monitoring

The DHT11 sensor continuously measures the surrounding temperature.

Temperature data can be:

- Displayed on the LCD
- Sent to the web dashboard
- Used for fire-condition detection

---

## 💧 Humidity Monitoring

The DHT11 sensor also measures the relative humidity of the surrounding environment.

Humidity information can be useful for understanding environmental conditions inside the building.

---

## 💨 Gas and Smoke Detection

The MQ-2 sensor is used for detecting smoke and combustible gases.

The sensor is sensitive to smoke and several flammable gases and provides a changing electrical output depending on the surrounding gas concentration.

---

## 🔥 Automatic Fire Detection

The ESP32 continuously evaluates the sensor measurements.

If the measured temperature rises beyond the predefined fire threshold, the system considers the situation to be a possible fire condition.

---

## 🧯 Autonomous Fire Extinguisher

When the programmed fire-detection condition is satisfied, the controller can activate the fire-extinguisher mechanism.

The prototype concept therefore reduces dependence on immediate human intervention.

> **Note:** The presentation describes an automatic fire-extinguisher/motor function but does not provide the detailed motor-driver, relay circuit, pump specification, or extinguisher actuator design.

---

## 📟 LCD Display

A local LCD display is used for presenting sensor information near the monitoring unit.

This enables local monitoring even without opening the remote web dashboard.

---

## 🌐 IoT Monitoring

The ESP32 includes integrated Wi-Fi capability and can be used to send sensor measurements to the IoT monitoring system.

Remote monitoring allows authorized personnel to observe building conditions from locations such as:

- Security room
- Maintenance room
- Building management room
- Fire-control room
- Remote monitoring station

---

## 🖥️ Web Dashboard

A web-based dashboard is designed to display monitoring information from different floors and locations.

The prototype interface includes parameters such as:

- Temperature
- Humidity
- AQI
- Gas Detector
- Fire Extinguisher Motor status

The demonstrated dashboard organizes sensors based on building floors and locations.

---

# 🏗️ System Architecture

```text
                  ┌──────────────────────┐
                  │     DHT11 Sensor     │
                  │ Temperature/Humidity │
                  └──────────┬───────────┘
                             │
                             │
                             ▼
                  ┌──────────────────────┐
                  │                      │
                  │     ESP32 / NodeMCU  │
                  │                      │
                  └──────────┬───────────┘
                             ▲
                             │
                  ┌──────────┴───────────┐
                  │      MQ-2 Sensor     │
                  │   Smoke/Gas Sensor   │
                  └──────────────────────┘

                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼

       ┌────────────┐  ┌─────────────┐  ┌──────────────┐
       │ LCD Display│  │ Wi-Fi / IoT │  │ Fire Control │
       └────────────┘  └──────┬──────┘  │   Mechanism  │
                              │         └──────────────┘
                              ▼
                     ┌──────────────────┐
                     │ Web Application  │
                     │ Monitoring Panel │
                     └──────────────────┘
```

---

# 🔄 Working Principle

The complete system can be represented as:

```text
              START
                │
                ▼
        Initialize ESP32
                │
                ▼
       Initialize Sensors
                │
                ▼
        Initialize LCD
                │
                ▼
       Connect to Network
                │
                ▼
      Read DHT11 Sensor
                │
                ├──► Temperature
                │
                └──► Humidity
                │
                ▼
       Read MQ-2 Sensor
                │
                ▼
       Process Measurements
                │
                ▼
        Display on LCD
                │
                ▼
       Send Data to Website
                │
                ▼
      Compare Temperature
       with Fire Threshold
                │
         ┌──────┴──────┐
         │             │
        NO            YES
         │             │
         │             ▼
         │     Fire Condition Detected
         │             │
         │             ▼
         │     Activate Extinguisher
         │
         └─────────────┐
                       │
                       ▼
              Continue Monitoring
```

---

# 🧰 Hardware Components

| Component | Purpose |
|---|---|
| ESP32 / NodeMCU | Main controller and Wi-Fi communication |
| DHT11 Sensor | Temperature and humidity measurement |
| MQ-2 Sensor | Smoke and combustible gas detection |
| LCD Display | Local display of sensor readings |
| Breadboard | Prototype circuit implementation |
| Jumper Wires | Electrical interconnections |
| Power Supply / USB | Powering and programming the ESP32 |
| Fire Extinguisher Motor / Actuator | Automatic extinguisher activation mechanism |

---

# 🧠 Main Controller — ESP32

The ESP32 is a low-cost and low-power microcontroller platform with integrated:

- Wi-Fi
- Bluetooth
- Digital GPIO
- Analog inputs
- Serial communication interfaces
- Processing capabilities

In this project, the ESP32 functions as the central controller.

It performs tasks such as:

```text
Sensor Data Acquisition
        ↓
Sensor Data Processing
        ↓
Threshold Comparison
        ↓
LCD Updating
        ↓
Fire Detection
        ↓
Extinguisher Control
        ↓
Wi-Fi Communication
        ↓
Web Dashboard Updating
```

---

# 🌡️ DHT11 Temperature and Humidity Sensor

The **DHT11** is a digital temperature and humidity sensor.

It contains:

- A capacitive humidity sensing element
- A temperature sensing element
- Digital signal-processing circuitry

The sensor provides a digital output to the ESP32.

## DHT11 Role in the Project

```text
Environment
    │
    ▼
 DHT11 Sensor
    │
    ├────────► Temperature
    │
    └────────► Humidity
                 │
                 ▼
               ESP32
```

The temperature measurement can also participate in the fire-detection logic.

---

# 💨 MQ-2 Smoke and Gas Sensor

The **MQ-2** is a smoke and combustible-gas sensor.

It is commonly used for detecting:

- Smoke
- LPG
- Propane
- Methane
- Hydrogen
- Other combustible gases

The presentation specifies a general detectable flammable-gas range of approximately:

```text
300 – 10,000 ppm
```

depending on gas type, calibration, sensor conditions, and implementation.

The MQ-2 sensing element changes conductivity when smoke or combustible gases are present.

---

# ⚠️ MQ-2 Calibration

The raw analog value of an MQ-2 sensor should not automatically be interpreted as an accurate gas concentration or standardized AQI value.

For reliable measurements, appropriate calibration is required.

The project presentation demonstrates gas sensor readings, but does not specify a complete calibration equation for converting MQ-2 output to an official AQI scale.

Therefore:

```text
MQ-2 Reading ≠ Standard AQI unless a validated conversion/calibration method is implemented.
```

---

# 📟 LCD Monitoring

The LCD provides local display capability.

Example displayed parameters may include:

```text
Temperature
Humidity
Gas Reading
System Status
```

Example concept:

```text
TEMP: 29.3 C
HUM : 71 %
GAS : 1047
STATUS: NORMAL
```

The actual prototype photographs demonstrate sensor readings displayed through the hardware monitoring setup.

---

# 🌐 Web-Based Monitoring System

The project also includes a web application for monitoring sensor parameters remotely.

The dashboard concept separates the commercial building into floors and monitoring locations.

Example:

```text
COMMERCIAL BUILDING

├── Ground Floor
│   ├── Location 1
│   ├── Location 2
│   └── Location 3
│
├── First Floor
│   ├── Location 1
│   ├── Location 2
│   └── Location 3
│
├── Third Floor
│   ├── Location 1
│   ├── Location 2
│   └── Location 3
│
└── Fourth Floor
    ├── Location 1
    ├── Location 2
    └── Location 3
```

For each location, the interface is designed to present:

```text
Temperature
Humidity
AQI
Gas Detector
Fire Extinguisher Motor
```

This architecture can be scaled so that multiple ESP32-based monitoring nodes are installed throughout the building.

---

# 💻 Software Used

The following software technologies were used in the project:

| Technology | Purpose |
|---|---|
| Arduino IDE | ESP32 programming and serial monitoring |
| HTML | Webpage structure |
| CSS | Webpage styling |
| React JS | Frontend user interface |
| Node JS | Web application/backend functionality |

---

# 🛠️ Development Tools

## Arduino IDE

Used for:

- Writing ESP32 firmware
- Compiling firmware
- Uploading firmware
- Serial debugging
- Sensor testing

---

## HTML

Used for defining the structure of the web monitoring interface.

---

## CSS

Used for styling components such as:

- Monitoring cards
- Floor layouts
- Sensor fields
- Buttons
- Headers
- Location panels

---

## React JS

React can be used for creating reusable dashboard components.

Example conceptual structure:

```text
App
│
├── Header
│
├── GroundFloor
│   ├── Location1
│   ├── Location2
│   └── Location3
│
├── FirstFloor
│
├── ThirdFloor
│
└── FourthFloor
```

---

## Node JS

Node JS can support communication between the IoT hardware and monitoring website.

Possible implementation responsibilities include:

```text
Receiving Sensor Data
        ↓
Processing Requests
        ↓
Providing Data to Frontend
        ↓
Updating Dashboard
```

The exact API architecture and database implementation are not documented in the provided project presentation.

---

# 📡 IoT Data Flow

```text
DHT11 ─────┐
            │
MQ-2 ───────┼────► ESP32
            │        │
            │        ├────► LCD Display
            │        │
            │        ├────► Fire Detection Algorithm
            │        │
            │        ├────► Extinguisher Control
            │        │
            │        └────► Wi-Fi
            │                   │
            │                   ▼
            │              Web Server
            │                   │
            │                   ▼
            └────────────► Web Dashboard
```

---

# 🔥 Fire Detection Logic

A simplified version of the project logic is:

```cpp
if (temperature > FIRE_THRESHOLD)
{
    fireDetected = true;
    activateFireExtinguisher();
}
else
{
    fireDetected = false;
}
```

The exact threshold value used in the original implementation is not specified in the presentation.

Therefore it should be configured based on:

- Building environment
- Sensor accuracy
- Fire-safety requirements
- Installation location
- Required detection sensitivity

---

# 🧯 Fire Extinguisher Control Logic

Conceptually:

```text
Normal Temperature
        │
        ▼
Extinguisher OFF
```

When abnormal temperature is detected:

```text
Temperature > Threshold
          │
          ▼
   Fire Detected
          │
          ▼
ESP32 Generates Control Signal
          │
          ▼
 Relay / Driver Stage
          │
          ▼
Fire Extinguisher Motor / Actuator
          │
          ▼
 Extinguishing Action
```

The detailed relay, motor driver, pump, solenoid, or mechanical extinguisher design is not specified in the original presentation.

---

# 🧪 Prototype Hardware

The prototype consists of:

- ESP32 development board
- DHT11 sensor module
- MQ-2 sensor module
- LCD display
- Breadboard
- Jumper wires
- USB power/programming connection

The prototype demonstrates successful integration of sensing and local monitoring hardware.

---

# 📊 Serial Monitor Output

The Arduino IDE Serial Monitor is used to verify real-time measurements.

The project demonstration contains output similar to:

```text
Humidity: 71.00 %
Temperature in Celsius: 29.30 °C
Temperature in Fahrenheit: 84.74 °F
GAS SENSOR READING: 1047

Humidity: 71.00 %
Temperature in Celsius: 29.30 °C
Temperature in Fahrenheit: 84.74 °F
GAS SENSOR READING: 1043

Humidity: 71.00 %
Temperature in Celsius: 29.30 °C
Temperature in Fahrenheit: 84.74 °F
GAS SENSOR READING: 1040
```

These readings demonstrate continuous sensor acquisition through the ESP32.

---

# 📈 Parameters Monitored

| Parameter | Sensor/System | Function |
|---|---|---|
| Temperature | DHT11 | Environmental and fire-condition monitoring |
| Humidity | DHT11 | Indoor environmental monitoring |
| Smoke/Gas | MQ-2 | Smoke and combustible-gas detection |
| AQI Field | Web Dashboard | Air-quality related monitoring display |
| Fire Status | ESP32 Logic | Fire-condition detection |
| Extinguisher Status | Control System | Automatic extinguisher monitoring |

---

# 🚨 Example System States

## Normal Condition

```text
Temperature = Normal
Humidity    = Normal
Gas Level   = Normal

        ↓

Fire Status = SAFE

        ↓

Extinguisher = OFF
```

---

## Possible Fire Condition

```text
Temperature > Preset Threshold

        ↓

Possible Fire Detected

        ↓

Extinguisher Control Activated

        ↓

Dashboard Updated
```

---

# 🏢 Multi-Floor Deployment Concept

One of the major advantages of the proposed architecture is the ability to deploy monitoring units throughout a commercial building.

Example:

```text
                    CONTROL ROOM
                         │
                         │
                   IoT Dashboard
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼

     Ground Floor    First Floor    Second Floor
         │               │               │
      ESP32 Node       ESP32 Node       ESP32 Node
         │               │               │
      Sensors         Sensors         Sensors
```

Each node can monitor its surrounding area and report sensor information to the centralized monitoring interface.

---

# 🔧 Hardware Connections

The original project presentation does not provide exact ESP32 GPIO assignments.

A typical implementation requires connections between:

```text
ESP32
│
├── DHT11 Data Pin
├── MQ-2 Analog/Digital Output
├── LCD Communication Pins
└── Fire Extinguisher Driver Output
```

Exact pins should match the corresponding firmware.

---

# 📂 Suggested Repository Structure

```text
IoT-Autonomous-Fire-Extinguisher/
│
├── README.md
│
├── firmware/
│   └── esp32_fire_monitoring.ino
│
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       ├── pages/
│       └── App.js
│
├── backend/
│   ├── server.js
│   ├── routes/
│   └── package.json
│
├── hardware/
│   ├── block-diagram/
│   ├── circuit-diagram/
│   └── prototype-images/
│
├── docs/
│   └── project-presentation/
│
└── images/
    ├── hardware-kit.jpg
    ├── dashboard.jpg
    └── serial-monitor.jpg
```

This repository layout is a recommended organizational structure and is not specified in the original presentation.

---

# 🚀 Installation

## 1. Install Arduino IDE

Download and install Arduino IDE.

Configure support for the ESP32 board.

---

## 2. Connect the ESP32

Connect the ESP32 to your computer using USB.

Select the appropriate:

```text
Board
Port
Upload Speed
```

in Arduino IDE.

---

## 3. Install Required Sensor Libraries

Depending on the implementation, libraries may be required for:

- DHT11
- LCD display
- ESP32 Wi-Fi communication

The exact library versions used by the original project are not specified in the presentation.

---

# 🖥️ Running the Web Application

For a typical React + Node JS implementation:

## Clone Repository

```bash
git clone <repository-url>
cd IoT-Autonomous-Fire-Extinguisher
```

---

## Install Frontend Dependencies

```bash
cd frontend
npm install
npm start
```

---

## Install Backend Dependencies

Open another terminal:

```bash
cd backend
npm install
node server.js
```

or:

```bash
npm start
```

> The original project's exact Node.js package configuration and API endpoints are not documented in the presentation.

---

# 🔌 ESP32 Firmware Workflow

The firmware generally performs the following operations:

```cpp
void setup()
{
    // Initialize Serial Monitor

    // Initialize DHT11

    // Initialize MQ-2

    // Initialize LCD

    // Initialize extinguisher control

    // Connect ESP32 to Wi-Fi
}

void loop()
{
    // Read temperature

    // Read humidity

    // Read gas sensor

    // Display sensor data

    // Send values to IoT dashboard

    // Check fire threshold

    // Activate extinguisher if required

    // Repeat continuously
}
```

This is a conceptual structure rather than the original firmware source code.

---

# ✅ Advantages

The proposed system provides several advantages:

- Automatic fire-condition detection
- Autonomous extinguisher activation
- Continuous temperature monitoring
- Continuous humidity monitoring
- Smoke/gas detection
- IoT-based remote monitoring
- Local LCD visualization
- Centralized monitoring of multiple locations
- Expandable architecture for multi-storey buildings
- Reduced dependence on constant manual supervision
- Real-time environmental observation

---

# ⚠️ Limitations

The prototype also has several practical limitations.

### 1. DHT11 Accuracy

DHT11 is a low-cost environmental sensor and may not provide the accuracy or response speed required for certified commercial fire-detection systems.

### 2. MQ-2 Calibration

MQ-2 measurements require calibration.

Raw sensor values should not automatically be interpreted as standardized air-quality or gas-concentration values.

### 3. Fire Detection Based on Temperature

Using a single temperature threshold alone can generate:

- False positives
- Delayed detection
- Missed events

A practical safety system should normally combine several detection methods.

### 4. Prototype-Level Implementation

The presented hardware is a prototype.

Commercial deployment would require industrial-grade:

- Sensors
- Fire detectors
- Power supplies
- Communications
- Enclosures
- Actuators
- Fail-safe mechanisms
- Certified extinguishing equipment

---

# 🔮 Future Scope

The project can be extended with several improvements.

## Multi-Sensor Fire Detection

Additional sensors can include:

- Flame sensor
- Dedicated smoke detector
- CO sensor
- CO₂ sensor
- PM2.5 sensor
- PM10 sensor
- Higher-accuracy temperature sensor

---

## Mobile Notifications

The system could send:

```text
🔥 FIRE ALERT

Location: First Floor - Location 2
Temperature: XX °C
Smoke Status: Detected
Gas Level: High
Extinguisher: Activated
```

through:

- SMS
- Email
- Mobile application
- Push notification

---

## Cloud Integration

Future versions could integrate:

- AWS IoT
- Firebase
- Azure IoT
- MQTT Broker
- Cloud databases

for large-scale building monitoring.

---

## Historical Data Analytics

Sensor data can be stored for:

- Temperature trends
- Humidity trends
- Gas-level trends
- Fire-event history
- Maintenance records
- Building air-quality analysis

---

## Machine Learning

Machine-learning models could be used to evaluate combinations of:

```text
Temperature
Humidity
Smoke
Gas concentration
Rate of temperature rise
Historical patterns
```

to improve detection accuracy.

---

## Building Automation Integration

The project could also interact with:

```text
Fire Alarm
      +
Ventilation System
      +
Air Purifier
      +
Emergency Lighting
      +
Building Management System
      +
Fire Extinguisher
```

---

# 🛡️ Safety Disclaimer

This project is an **educational/research prototype**.

It should **not be treated as a replacement for certified commercial fire-alarm or fire-suppression systems**.

Real commercial-building fire protection must comply with applicable:

- Fire codes
- Electrical codes
- Building codes
- Safety standards
- Local authority requirements

and should use properly certified fire-detection and suppression equipment.

---

# 🎓 Project Team

**Vishnu Institute of Technology (Autonomous)**  
**Department of Electrical and Electronics Engineering**

### Team Members

| Student ID | Name |
|---|---|
| 19PA1A0231 | G. Sai Anirudh |
| 20PA5A0206 | J. Uma Gayathri |
| 19PA1A0237 | G. Prem Pavan |
| 19PA1A0213 | B. Divya Manikanta |
| 19PA1A0224 | D. Veneela |

### Project Guide

**Mrs. I. V. V. Vijetha, M.Tech (PhD)**  
Assistant Professor  
Department of Electrical and Electronics Engineering  
Vishnu Institute of Technology (Autonomous)

---

# 📝 Project Summary

The project demonstrates an IoT-enabled safety platform that combines environmental monitoring with automatic fire-response capabilities.

The overall operation can be summarized as:

```text
Sense
  ↓
Monitor
  ↓
Analyze
  ↓
Detect
  ↓
Notify
  ↓
Actuate
```

The ESP32 acts as the central processing and communication unit, while the DHT11 and MQ-2 provide environmental sensor measurements.

Local readings are displayed using an LCD, while an IoT web dashboard provides centralized monitoring of multiple floors and locations.

When the configured fire-condition threshold is exceeded, the system is designed to activate the fire-extinguishing mechanism automatically.

---

# 📚 Technologies

![ESP32](https://img.shields.io/badge/ESP32-IoT-red)
![Arduino](https://img.shields.io/badge/Arduino-IDE-blue)
![React](https://img.shields.io/badge/React-JS-blue)
![NodeJS](https://img.shields.io/badge/Node-JS-green)
![HTML](https://img.shields.io/badge/HTML-5-orange)
![CSS](https://img.shields.io/badge/CSS-3-blue)
![IoT](https://img.shields.io/badge/Internet%20of%20Things-IoT-purple)

---

# ⭐ Conclusion

The **IoT-Based Autonomous Fire Extinguisher, Temperature and AQI Monitoring System for Commercial Buildings** demonstrates how IoT technology can be applied to building safety and environmental monitoring.

By combining:

- ESP32
- DHT11
- MQ-2
- LCD display
- IoT communication
- Web monitoring
- Automated extinguisher control

the system provides a foundation for developing intelligent fire-safety solutions for commercial and multi-storey buildings.

---

## 📜 License

This project was developed for academic and educational purposes.

If the repository is made public, an appropriate open-source license such as the MIT License may be added depending on the authors' requirements.

---

## 🤝 Contributions

Suggestions and improvements to the project are welcome.

Possible contribution areas include:

- Improved sensor calibration
- Better dashboard design
- MQTT integration
- Cloud integration
- Mobile notifications
- Improved fire-detection algorithms
- Hardware PCB design
- Multi-floor deployment
- Data analytics

---

## ⭐ Support

If you find this project useful, consider giving the repository a **star ⭐**.

---

### 🔥 IoT + Embedded Systems + Fire Safety + Smart Buildings

**Developed as an academic project by the Department of Electrical and Electronics Engineering, Vishnu Institute of Technology (Autonomous).**
