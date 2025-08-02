# HEATER-CONTROL-SYSTEM

This project simulates a temperature-controlled heater system using an ESP32,DHT22 sensor,I2C LCD,LED indicators,buzzer, and a 10-segment LED bar graph. The system manages heater states (`Idle`, `Heating`, `Stabilizing`, `Target Reached`, `Overheat`) using FreeRTOS tasks and logs data via UART.
To observe the full behavior of the system (state changes, LED indicators, buzzer alerts, etc.),vary the temperature readings from the DHT22 sensor. In the Wokwi simulator, click on the DHT22 sensor and adjust the temperature manually. This will trigger the heater control logic and reflect the changes in system states.

---

# Simulation Platform

- [Wokwi ESP32 Simulator](https://wokwi.com)

---

# Features

- Real-time temperature reading using DHT22
- Heater control logic using defined temperature thresholds
- Multiple system states:
  - `IDLE`
  - `HEATING`
  - `STABILIZING`
  - `TARGET_OK`
  - `OVERHEAT`
- Visual indicators:
  -  LED for overheat status
  -  LED for idle status
  -  Buzzer for overheat warning
  -  LCD to display current temperature and system state
  -  10-segment LED bar graph to show heating level
- UART logging to simulate BLE advertisement (Wokwi only)

---

# Pin Configuration

| Component       | GPIO Pin |
|-----------------|-----------|
| DHT22 Data Pin  | 18        |
| Overheat LED    | 25        |
| Idle LED        | 26        |
| Buzzer          | 23        |
| I2C LCD SDA     | 21        |
| I2C LCD SCL     | 22        |
| LED Bar Graph   | 27, 19, 17, 16, 15, 14, 12, 5, 4, 2 |

---

# Temperature Thresholds

| State         | Condition                     |
|---------------|-------------------------------|
| `HEATING`     | Temp < 20.0°C                 |
| `STABILIZING` | 20.0°C ≤ Temp < 28.0°C        |
| `TARGET_OK`   | Temp == 28.0°C                |
| `OVERHEAT`    | Temp ≥ 45.0°C                 |

---

# Heater Control Logic

- Activates red LED if in `OVERHEATING` state
- Turns on green LED if system is stable
- Buzzer activates in `OVERHEATING` state
- LED bar graph shows current heating level

---

# FreeRTOS Tasks

| Task Name     | Description                                |
|---------------|--------------------------------------------|
| `tempTask`    | Reads temperature from DHT22               |
| `controlTask` | Updates heater logic, state, LEDs, LCD     |
| `bleTask`     | Sends mock BLE advertising via Serial UART |

---


