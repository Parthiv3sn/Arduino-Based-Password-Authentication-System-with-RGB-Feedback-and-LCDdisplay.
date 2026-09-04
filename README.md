# Arduino Password Authentication System

An Arduino keypad-style password demonstration using ten buttons, a 16×2 I²C LCD, and red/green status LEDs.

> This is a learning project, not a secure access-control system. The password is stored in plain text in volatile memory and is displayed as entered.

## Features

- Numeric button input
- LCD prompts and access result
- Red LED for denied access and green LED for granted access
- Four-digit password update mode

## Hardware

- Arduino Uno or compatible board
- 16×2 I²C LCD (address `0x27`)
- 10 momentary push-buttons
- Red and green LEDs with current-limiting resistors

## Wiring

| Function | Arduino pin |
| --- | --- |
| Digit buttons 0–9 | 2–11 |
| Red / green LED | 12 / 13 |
| LCD | I²C SDA / SCL |

Buttons use `INPUT_PULLUP`; wire each button between its pin and GND.

## Setup

1. Install the **LiquidCrystal_I2C** library.
2. Open `Source Code` (rename it to `PasswordSystem.ino` if needed).
3. Confirm the LCD I²C address and upload.

## Security and design notes

- The initial password is `1234`; it resets after power loss because EEPROM is not used.
- Password digits are shown on the LCD. Mask them for a better user experience.
- The current setup button shares pin 2 with digit 0. Use a separate pin for password-change mode before deploying.
- Add a relay or servo output if the project is intended to operate a physical lock.
- Add rate limiting, a lockout after failed attempts, and EEPROM-backed storage for a stronger demonstration.

## Project files

- `Source Code` — Arduino sketch
- `Circuit.png` — wiring reference
