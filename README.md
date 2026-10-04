# Laboratory Activity 3: GPIO and Button Control

## Overview

This laboratory activity demonstrates the use of **GPIO (General Purpose Input/Output)** on an ESP32 microcontroller. A push button is used as a digital input to control two LEDs as digital outputs.

The button uses the ESP32's internal pull-up resistor through `INPUT_PULLUP`. When the button is pressed, the two LEDs change their states using an `if/else` condition.

## Features

- Uses ESP32 GPIO pins for digital input and output
- Uses the internal pull-up resistor on GPIO 23
- LED 1 turns **ON** when the button is released
- LED 2 turns **ON** when the button is pressed
- Uses an `if/else` statement for button control
- Demonstrates basic digital GPIO operation

## Components

- ESP32 development board
- Tactile push button
- 2 × LEDs
- 2 × 100Ω resistors
- Breadboard
- Jumper wires
- USB cable

## Wiring

### Push Button

- Button terminal 1 → ESP32 GPIO 23
- Button terminal 2 → GND

### LED 1

- Anode → GPIO 18 through a 100Ω resistor
- Cathode → GND

### LED 2

- Anode → GPIO 19 through a 100Ω resistor
- Cathode → GND

## Circuit Diagram

<img src="./circuit-diagram.png" width="828" alt="ESP32 GPIO and button control circuit diagram" />

## Project Setup

<img src="./0e73ad4f-2b6d-4a9a-9653-0d8363593c35.jpg" width="490" alt="Actual project setup" />

<img src="./5dc8f2cc-fa6d-4328-a0e0-7b14e3ad908c.jpg" width="490" alt="Actual project setup" />

<img src="./6ac119c6-5a0d-408e-ae6a-f07a8956d50c.jpg" width="490" alt="Actual ESP32 project setup" />

## Source Code

```cpp
#include <Arduino.h>

const uint8_t BUTTON_PIN = 23;
const uint8_t LED1_PIN = 18;
const uint8_t LED2_PIN = 19;

void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED1_PIN, OUTPUT);
  pinMode(LED2_PIN, OUTPUT);

  digitalWrite(LED1_PIN, HIGH);
  digitalWrite(LED2_PIN, LOW);
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {
    digitalWrite(LED1_PIN, LOW);
    digitalWrite(LED2_PIN, HIGH);
  } else {
    digitalWrite(LED1_PIN, HIGH);
    digitalWrite(LED2_PIN, LOW);
  }
}