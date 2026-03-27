# 🌾 Smart Crop Disease & Risk Predictor

An ESP32-based crop monitoring system that detects disease risk in real 
time using temperature and humidity data — and automatically acts on it.

## What it does
- Reads temperature & humidity every 10 seconds using a DHT11 sensor
- Runs a rule-based algorithm to predict disease risk: Low / Medium / High
- Shows live crop advisory on a 0.96" OLED screen
- Auto-activates a relay-driven water pump when risk turns High
- Sends instant Telegram alerts to your phone (under 2 sec)
- Logs data to ThingSpeak cloud with a 7-day risk trend graph via MQTT

## Tech Stack
| Layer    | Tools Used                              |
|----------|-----------------------------------------|
| Hardware | ESP32, DHT11, OLED SSD1306, Relay Module|
| Protocols| I2C, MQTT, Wi-Fi                        |
| Cloud    | ThingSpeak, Telegram Bot API            |
| Language | C++ (Arduino framework)                 |

## How the risk algorithm works
| Condition                          | Risk   | Action              |
|------------------------------------|--------|---------------------|
| Temp > 30°C and Humidity > 80%     | High   | Pump ON + Alert sent|
| Temp > 25°C and Humidity > 65%     | Medium | Warning on OLED     |
| Everything else                    | Low    | No action           |

## Circuit
- DHT11        → GPIO4
- OLED SSD1306 → SDA: GPIO21, SCL: GPIO22
- Relay        → GPIO26

## Setup
1. Clone this repo
2. Open in Arduino IDE
3. Add Wi-Fi credentials, Telegram Bot token & ThingSpeak API key in config.h
4. Flash to ESP32 — done

Built as part of my embedded systems learning journey 🚀
