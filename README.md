# Laboratory Activity 3: GPIO and Button Control

## Overview

This project demonstrates the use of GPIO pins for digital input and output using an ESP32 microcontroller. A push button is used to control two LEDs that work in opposite states. The activity uses the internal pull-up resistor (`INPUT_PULLUP`) and `if/else` statements to control the LEDs based on the button's condition.

## Project Features

* **Internal Pull-Up Resistor:** Uses `INPUT_PULLUP` on GPIO 23 to keep the input HIGH when the button is released.
* **Opposite LED Behavior:** LED 1 turns ON when the button is released, while LED 2 turns ON when the button is pressed.
* **If/Else Statements:** Uses conditional statements to control the LEDs.
* **Digital Input and Output:** Demonstrates how a push button and LEDs work with GPIO pins.

## Hardware Components

* 1x ESP32 Microcontroller
* 1x Tactile Push Button
* 2x LEDs
* 2x 100Ω Resistors
* 1x Breadboard
* Jumper Wires
* 1x USB Cable

## Pin Wiring Connections

| Component   | Pin         | Connection                      |
| ----------- | ----------- | ------------------------------- |
| Push Button | Terminal 1  | GPIO 23                         |
| Push Button | Terminal 2  | GND                             |
| LED 1       | Anode (+)   | GPIO 18 through a 100Ω resistor |
| LED 1       | Cathode (-) | GND                             |
| LED 2       | Anode (+)   | GPIO 19 through a 100Ω resistor |
| LED 2       | Cathode (-) | GND                             |

## Circuit Diagram

**Disclaimer:** The image below is intended for documentation and reference purposes. Your actual circuit setup may look different depending on your wiring and components.

<img width="828" height="343" alt="image" src="https://github.com/user-attachments/assets/8cf218b7-205e-4201-8148-3a6a160d3db7" />


## Project Setup

**Disclaimer:** The following image is a placeholder for the actual hardware setup. Replace it with your own project photo to show your completed activity.

<img width="490" height="428" alt="image" src="https://github.com/user-attachments/assets/cbbf6543-ca03-4700-9aef-237fe1ee28f2" />


## Source Code

```cpp
#include <Arduino.h>

const uint8_t BUTTON_PIN = 23;
const uint8_t LED1_PIN = 18;
const uint8_t LED2_PIN = 19;

void setup() {
  // Enable the internal pull-up resistor
  pinMode(BUTTON_PIN, INPUT_PULLUP);

  pinMode(LED1_PIN, OUTPUT);
  pinMode(LED2_PIN, OUTPUT);

  // Set the initial LED states
  digitalWrite(LED1_PIN, HIGH);
  digitalWrite(LED2_PIN, LOW);
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);

  // Check the button state
  if (buttonState == LOW) {
    // When the button is pressed
    digitalWrite(LED1_PIN, LOW);
    digitalWrite(LED2_PIN, HIGH);
  } else {
    // When the button is released
    digitalWrite(LED1_PIN, HIGH);
    digitalWrite(LED2_PIN, LOW);
  }
}
```

## Observation Summary

| Button State | Input Logic | LED 1 (GPIO 18) | LED 2 (GPIO 19) |
| ------------ | ----------- | --------------- | --------------- |
| Released     | HIGH        | ON              | OFF             |
| Pressed      | LOW         | OFF             | ON              |

## How to Run the Project

1. Connect the ESP32 and other components based on the wiring table.
2. Connect the ESP32 to your computer using a USB cable.
3. Open the project in Arduino IDE or PlatformIO.
4. Select the correct ESP32 board and COM port.
5. Upload the source code to the ESP32.
6. Wait for the board to restart.
7. Observe the LEDs and press the push button to test their behavior.

## Expected Output

* When the button is released, LED 1 turns ON and LED 2 turns OFF.
* When the button is pressed, LED 1 turns OFF and LED 2 turns ON.
* The LEDs change their states depending on the button's condition.

## Conclusion

This activity demonstrates how GPIO pins work as digital inputs and outputs. By using the internal pull-up resistor and `if/else` statements, the push button can control two LEDs with opposite behavior. It also provides a basic understanding of how to read button inputs and control electronic components using an ESP32.

## Disclaimer

This README file is intended for educational and documentation purposes. The images and circuit diagrams should represent the actual project whenever possible. Any sample images or placeholders should be replaced with the actual results of the activity.
