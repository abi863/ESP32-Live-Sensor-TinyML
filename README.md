# ESP32 Live Sensor + TinyML Light Classification

## Aim

To connect an LDR sensor to an ESP32 and use an on-device TinyML model to classify light intensity as Dark, Normal, or Bright, with the result displayed on an OLED screen.

## Components Required

* ESP32 Development Board
* LDR (Light Dependent Resistor)
* 10 kΩ Resistor
* SSD1306 OLED Display (128 × 64, I2C)
* Breadboard
* Jumper Wires

## Technologies Used

* Arduino C++
* Python
* TensorFlow
* TensorFlow Lite
* TensorFlow Lite Micro
* Google Colab
* Wokwi Simulator

## System Architecture

LDR Sensor → ESP32 Analog Input → TinyML Model Inference → Light Classification → OLED Display

## Pin Connections

### LDR Sensor

* 3.3V → LDR
* LDR and 10 kΩ resistor junction → GPIO 34
* 10 kΩ resistor → GND

### OLED Display

| OLED Pin | ESP32 Pin |
| -------- | --------- |
| VCC      | 3.3V      |
| GND      | GND       |
| SDA      | GPIO 21   |
| SCL      | GPIO 22   |

## Machine Learning Model

A small neural network is trained using TensorFlow in Google Colab. The trained model is converted into TensorFlow Lite format and embedded into the ESP32 program as a C/C++ header file.

## Classification Categories

* Dark – Low light intensity
* Normal – Medium light intensity
* Bright – High light intensity

The initial model uses synthetic training data for demonstration. For reliable real-world classification, the model should be trained and calibrated using actual LDR readings.

## Working Principle

1. The LDR senses the surrounding light intensity.
2. The ESP32 reads the analog value from the sensor.
3. The input value is normalized according to the model's training format.
4. The TinyML model performs inference directly on the ESP32.
5. The predicted light category is displayed on the OLED screen.
6. The sensor reading and classification are updated periodically.

## Features

* Real-time light intensity measurement
* On-device TinyML inference
* Three-class light classification
* Live OLED display
* Offline inference without cloud connectivity
* Embedded machine learning implementation

## Expected Output

```text
LIVE LIGHT CLASSIFIER
---------------------
ADC: 850

Prediction:
Dark
```

Note: The displayed reading and classification are illustrative. Actual output depends on the sensor reading and trained model.

## Future Enhancements

* Train the model using real-world LDR measurements.
* Add data logging through the Serial Monitor.
* Display prediction confidence scores.
* Add Wi-Fi-based monitoring.
* Optimize the model for reduced memory usage.

## Result

The LDR sensor is interfaced with the ESP32, and a TinyML model performs on-device light classification. The predicted category is displayed on the OLED screen.

## Project Type

Embedded Systems, Internet of Things (IoT), TinyML, and Edge AI
