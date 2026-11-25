# Multi-Feature Advanced Morse Wireless Adapter <img width="60" alt="morse-key-signal-icon-minimalist-260nw-2851649717" src="https://github.com/user-attachments/assets/35ba05e1-7829-4261-bcf2-3cc039d2356a" />


A wireless Morse key interface built around an **esp32mini microcontroller**. Connect a straight key or paddle and use it as a BLE keyboard with Notepad, supported browser-based Morse tools, or compatible Android apps.

**Bluetooth device name:** `MorseBle`  
**Connection:** BLE keyboard; no separate driver installation is intended  
**Power:** USB Type-C from a computer or a suitable power bank



## Features

- Supports straight keys and dual-paddle keys.
- Selects a mode at startup with a five-way DIP switch.
- Types decoded Morse text into Notepad in the two Notepad modes.
- Sends configurable keyboard keys for browser and mobile Morse practice tools.
- Includes a buzzer & a status LED.
- Enable/Disable the buzzer using a jumper.
- Can be powered from a computer or a power bank.

## Quick start

1. Set the DIP switches to the desired mode before powering the device.
2. Connect power using the USB Type-C cable.
3. Pair/connect to the BLE keyboard named **MorseBle**. The device waits for this connection before reading the DIP switches.
4. The device reads the DIP setting once during startup. To change modes later, set the switches and reboot/reset the device.
5. For Notepad mode, open Notepad and focus its text area during the five-second startup pause. The device then types its heading and is ready for Morse input.
6. For browser mode, open the target site, configure its keyer settings, join or start a session as needed, and keep that page focused. The site receives the key presses from the device.

>Only one host should be connected over Bluetooth at a time. Disconnect the current host before connecting another computer or phone.

## DIP switch modes

The switch pins are GPIO 4, 5, 6, 7, and 10, in SW1-to-SW5 order. They use internal pull-ups: **0 = OFF/open**, **1 = ON/closed to GND**. SW1 is the least-significant bit when the firmware calculates the DIP value.

| DIP value | SW1 | SW2 | SW3 | SW4 | SW5 | Selected mode | Key behavior / speed |
|---:|:---:|:---:|:---:|:---:|:---:|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | Notepad straight key | 10 WPM |
| 1 | 1 | 0 | 0 | 0 | 0 | Notepad paddle | 12 WPM |
| 3 | 1 | 1 | 0 | 0 | 0 | VBand Type 1 | Configurable on the website |
| 7 | 1 | 1 | 1 | 0 | 0 | VBand Type 2 | Configurable on the website |
| 15 | 1 | 1 | 1 | 1 | 0 | VBand Type 3 | Configurable on the website |
| 31 | 1 | 1 | 1 | 1 | 1 | VBand Type 4 | Configurable on the website |


## Wiring 

All key contacts close to GND when pressed. The straight key uses GPIO 0. For a paddle, DIT uses GPIO 0 and DAH uses GPIO 1; both inputs use internal pull-ups.

| Connection | Pin | Behavior |
|---|---:|---|
| Straight key | GPIO 0 to GND | Active-low input |
| Paddle DIT | GPIO 0 to GND | Active-low input |
| Paddle DAH | GPIO 1 to GND | Active-low input |
| Buzzer | GPIO 3 | Circuit-side SPST switch controls buzzer enable |
| Onboard LED | GPIO 8 | Inverted logic: LOW turns it on |
| External LED | GPIO 20 | Normal logic: HIGH turns it on |
| DIP switch bank | GPIO 4, 5, 6, 7, 10 | `INPUT_PULLUP`; ON connects the input to GND |

In Notepad straight-key mode, the indicators follow the physical key. In the Notepad paddle mode, the buzzer and LEDs follow the generated Morse elements. In the browser keyboard modes, they follow the pressed key/paddle contacts.

## Browser tools

These are the browser destinations and key modes recorded for the project. Configure Morse key type and WPM in each site's settings where available. Keep the browser page focused while sending.

| Website | Straight key | Paddle | Firmware mode |
|---|:---:|:---:|---|
| [VBand](https://hamradio.solutions/vband/) | Yes | Yes | Type 1 |
| [Vail](https://vail.woozle.org/) | Yes | Yes | Type 2 |
| [Vail Morse](https://vailmorse.com/) | Yes | Yes | Type 2 |
| [Morse Me Please](https://morsemeplease.com/) | No | Yes | Type 3 |
| [CW Bot](https://cw-bot.hamradioduo.com/) | Yes | Yes | Type 1 |
| [CW Checker](https://tools.hamradioduo.com/cw-checker/) | Yes | Yes | Type 1 |
| [Morse Code World keyer](https://morsecode.world/international/trainer/keyer.html) | Yes | Yes | Type 4 |
| [Morse Halb](https://morse.halb.it/) | Yes | Yes | Type 3 |
| [CW Open Shack chat](https://cw.openshack.com/cwchat/) | Yes | Yes | Type 4 |

## Android apps

Configure the key type and WPM in the app where those options are available.

| App | Straight key | Paddle | Firmware mode |
|---|:---:|:---:|---|
| [Morse](https://play.google.com/store/apps/details?id=com.mweutbycjynwq.morse&hl=en_IN) | Yes | No | Type 1 |
| [Morse Keyer](https://play.google.com/store/apps/details?id=com.qft8.morsekeyer&hl=en_IN) | Yes | Yes | Type 1 |
| [Morse Chat](https://play.google.com/store/apps/details?id=digital.dong.morsechat&hl=en_IN) | Yes | No | Type 1 |

## Photos and wiring diagrams

Add project photos and wiring illustrations in this section when they are ready.

### PCB photos

`[PCB front photo placeholder — add image here]`

`[PCB back photo placeholder — add image here]`

### Straight-key 3.5 mm jack wiring

`[Straight-key 3.5 mm jack pinout placeholder — add image here]`

### Paddle 3.5 mm jack wiring

`[Paddle 3.5 mm jack pinout placeholder — add image here]`

## Firmware files

The current source files are in this folder. Open `cpo.ino` with the accompanying headers and `dictionary.h` in the Arduino IDE. The BLE device name is set in the main sketch as `MorseBle`.

## Notes

- The mode is sampled once after BLE connects. Reboot after changing DIP switches.
- Disconnect one computer/phone before pairing the adapter with another host.
- Slight warmth during BLE operation has been observed on the prototype.

