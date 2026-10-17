# IoT Temperature & Humidity Alarm (ESP32 + MQTT)

ESP32 IoT sensor node simulated in Wokwi, written in C++. A DHT22 sensor reads temperature and humidity, publishes JSON to an MQTT broker over WiFi, and sounds a buzzer alarm when a value goes above its limit.

## How it works
1. The DHT22 measures temperature and humidity
2. The ESP32 reads it every 2 seconds
3. It publishes a message such as `{"temp":24.0,"hum":40.0,"alarm":0}` to an MQTT topic
4. If temperature is above 35 °C or humidity is above 70 %, the alarm flag becomes 1 and the buzzer beeps three times

## Hardware (simulated)
ESP32 DevKit, DHT22 sensor on D15, buzzer on D13

## Files
- `sketch.ino`: the program
- `diagram.json`: the circuit wiring for Wokwi
- `libraries.txt`: required libraries (PubSubClient, DHT sensor library)

## Test results
| Test | Sensor setting | Result |
|---|---|---|
| Normal | 24 °C, 40 % | No alarm, `"alarm":0` |
| High temperature | 60.5 °C | `"alarm":1`, "ALARM: temperature too high", buzzer sounds |
| High humidity | 78 % | `"alarm":1`, "ALARM: humidity too high" |
| Back to normal | 26.5 °C, 66.5 % then 52.5 % | `"alarm":0`, alarm clears |

## Run it
Live simulation: (paste your Wokwi link here)

## Screenshots
Normal operation:
![Code and circuit](IoT%20sensor%201.jpeg)
![Normal readings](IoT%20sensor%202.jpeg)

Temperature alarm:
![Temperature alarm](IoT%20sensor%203.jpeg)

Humidity alarm and recovery:
![Humidity alarm](Iot%20sensor%204.jpeg)
![Back to normal](Iot%20sensor%205.jpeg)
