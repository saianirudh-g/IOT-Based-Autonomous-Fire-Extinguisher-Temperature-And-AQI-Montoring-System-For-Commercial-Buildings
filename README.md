# IoT-Based Autonomous Fire Extinguisher, Temperature, and AQI Monitoring System

This repository contains the firmware, hardware architecture, and setup instructions for an autonomous IoT safety system designed for commercial buildings. The system continuously monitors environmental parameters (Temperature, Humidity, and Air Quality Index) and autonomously deploys a fire extinguishing mechanism upon detecting a flame, while simultaneously pushing real-time data and alerts to a remote cloud dashboard.

## System Features

*   **Autonomous Fire Suppression:** Uses IR flame sensors to detect fire and automatically triggers a relay-controlled water pump or solenoid valve.
*   **Real-Time Air Quality Monitoring:** Measures hazardous gas concentrations and calculates the Air Quality Index (AQI) to ensure building safety compliance.
*   **Climate Tracking:** Monitors ambient temperature and humidity to detect abnormal heat spikes preceding a fire.
*   **IoT Cloud Dashboard:** Live telemetry monitoring and historical data logging via platforms like Blynk, ThingSpeak, or AWS IoT.
*   **Local Alarms & Display:** Triggers an on-site buzzer and updates an OLED display for immediate localized warning.
*   **Automated Email/SMS Alerts:** Sends emergency notifications to building administrators when thresholds are breached.

---

## Hardware Requirements

| Component | Function |
| :--- | :--- |
| **ESP32 Development Board** | Main microcontroller with built-in Wi-Fi/Bluetooth |
| **MQ-135 Gas Sensor** | Detects NH3, NOx, alcohol, benzene, smoke, and CO2 |
| **DHT22 / DHT11 Sensor** | Measures ambient temperature and relative humidity |
| **IR Flame Sensor(s)** | Detects infrared light emitted by open flames |
| **5V Relay Module (1-Channel)** | Acts as an electronic switch for the extinguishing system |
| **Mini Water Pump / Solenoid**| Deploys water or suppressant onto the fire |
| **0.96" I2C OLED Display** | Local visual display for sensor readings |
| **Active Buzzer** | Emits high-decibel audio alarm |
| **Power Supply** | 5V/2A power source for the ESP32, Sensors, and Relay |

---

## Software & Library Requirements

1.  **Arduino IDE** (v1.8.19 or v2.x)
2.  **ESP32 Board Package** installed via Arduino Boards Manager
3.  **Required Libraries:**
    *   `DHT sensor library` by Adafruit
    *   `Adafruit Unified Sensor`
    *   `Blynk` (if using Blynk IoT platform)
    *   `PubSubClient` (if using custom MQTT broker)
    *   `Adafruit_GFX` & `Adafruit_SSD1306` (for OLED display)

---

## Circuit Connections

*Note: Pinout is based on a standard ESP32 development board. Adjust pins in the code if using a different microcontroller.*

| Component Pin | ESP32 Pin | Notes |
| :--- | :--- | :--- |
| DHT22 `DATA` | `GPIO 4` | Requires a 10k pull-up resistor to 3.3V |
| MQ-135 `AOUT` | `GPIO 34 (A0)` | Analog input for variable gas concentration |
| Flame Sensor `DOUT` | `GPIO 14` | Digital output (Active Low when fire detected) |
| Relay `IN` | `GPIO 26` | Controls the water pump |
| Buzzer `+` | `GPIO 27` | Audible alarm |
| OLED `SDA` | `GPIO 21` | I2C Data |
| OLED `SCL` | `GPIO 22` | I2C Clock |

*All sensors should share a common Ground (GND). Ensure the water pump is powered by a separate, adequately rated power supply connected through the relay.*

---

## Installation and Setup

### 1. Hardware Assembly
1. Connect all sensors to the ESP32 as per the Circuit Connections table.
2. Connect the relay module to the water pump. Ensure the high-voltage/high-current circuit is securely isolated.
3. Power the ESP32 and ensure the sensors are receiving 3.3V/5V as required.

### 2. Cloud Configuration (e.g., Blynk)
1. Create a new template in the Blynk Web Dashboard.
2. Set up Datastreams:
   *   **V0 (Virtual Pin):** Temperature (Float)
   *   **V1:** Humidity (Float)
   *   **V2:** AQI Level (Integer)
   *   **V3:** Fire Status (String/LED)
3. Copy the `BLYNK_TEMPLATE_ID`, `BLYNK_DEVICE_NAME`, and `BLYNK_AUTH_TOKEN`.

### 3. Firmware Flashing
1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/yourusername/IoT-Autonomous-Fire-Extinguisher.git](https://github.com/yourusername/IoT-Autonomous-Fire-Extinguisher.git)
