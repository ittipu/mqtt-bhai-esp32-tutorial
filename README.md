# ESP32 Two-Way MQTT Communication with MQTT Bhai App 

[![Play Store](https://img.shields.io/badge/Download-MQTT_Bhai-green?logo=google-play)](https://play.google.com/store/apps/details?id=io.iotbhai.mqtt)
[![YouTube](https://img.shields.io/badge/Watch-Video_Tutorial-red?logo=youtube)](#) 
A complete, step-by-step IoT project demonstrating two-way MQTT communication using an **ESP32**, a **Raspberry Pi Local Broker**, our free public cloud broker, and the **MQTT Bhai** Android app. 

This project shows you how to publish structured JSON sensor data to a dashboard and subscribe to command topics to control physical hardware (onboard LED) in real-time.

## ✨ Features
* **Two-Way Communication:** Send sensor data from the ESP32 and receive control commands back.
* **JSON Telemetry:** Publishes structured data (Temperature, Humidity, RSSI, Uptime).
* **Zero-Latency Control:** Instantly toggle the ESP32's onboard LED via the app.
* **Dual Broker Setup:** Works with a local Raspberry Pi broker or the free public cloud broker (`mqtt.iotbhai.io`).

## 🛠️ Hardware & Software Requirements
* **ESP32 Development Board** (or similar compatible board)
* **Raspberry Pi** (Optional: for hosting a local Mosquitto broker)
* **Arduino IDE** (or PlatformIO)
* **[MQTT Bhai Android App](https://play.google.com/store/apps/details?id=io.iotbhai.mqtt)**

## 📡 MQTT Architecture & Topics

### 1. Telemetry Data (ESP32 -> App)
The ESP32 publishes sensor data as a JSON payload.
* **Topic:** `esp32/01/status` *(You can customize this)*
* **Example Payload:**
    ```json
    {
      "device": "SN_01",
      "uptime": 315,
      "wifi_rssi": -36,
      "temp": 25,
      "hum": 59
    }
    ```

### 2. Command Control (App -> ESP32)
The ESP32 subscribes to a command topic to control the onboard LED.
* **Topic:** `esp32/01/cmd`
* **Payloads Expected:** `on` to turn the LED on, `off` to turn it off.

## 📱 Setting Up the MQTT Bhai App

1.  Download **MQTT Bhai** from the [Google Play Store](https://play.google.com/store/apps/details?id=io.iotbhai.mqtt).
2.  Open the app and click **Add Broker**.
3.  **Broker Address:** * *For Cloud:* `mqtt.iotbhai.io` (Port `1883`)
    * *For Local:* Your Raspberry Pi's IP Address (e.g., `192.168.1.100`, Port `1883`)
4.  Navigate to the **Dashboard** or **Subscribe** tab.
5.  Subscribe to `esp32/01/status` to view the incoming JSON data.
6.  Create a publish button/card for topic `esp32/01/cmd` with the payloads `on` and `off` to control the LED.

## 💻 ESP32 Code Setup
1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
