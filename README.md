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

### Device
<p align="center">
<img src="https://github.com/user-attachments/assets/6b839d7d-ead8-4452-95cd-797ae7ca1826" width="25%" alt="top view">
</p>

### Straight-key 3.5 mm jack wiring
<p align="center">
<img src="https://github.com/user-attachments/assets/8b1792ce-840f-46e9-8743-4f775d8a575c" width="40%" alt="3 5mm TRS Straight Key Pinout">
</p>

### Paddle 3.5 mm jack wiring
<p align="center">
<img src="https://github.com/user-attachments/assets/3c18822b-4436-4d8e-9915-a3711d87c0c7" width="40%" alt="3 5 mm TRS Paddle Key Pinout">
</p>

### Buzzer J1
<p align="center">
<img src="https://github.com/user-attachments/assets/85cffd90-2701-4e6c-a52a-3f6ec9b9174d" width="10%" alt="jumper conn">
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/3774796b-c42f-4b88-aefd-515785695b76" width="30%" alt="Jumper Open and Closed Buzzer States">
</p>

<br>
<br>

### Adding MorseBle 
#### PC --> Bluetooth & devices > Devices
<p align="center">
<img width="50%" alt="ble device" src="https://github.com/user-attachments/assets/9a671d66-ee57-4d2b-9e16-baf136012bd6" />
</p>

#### Phone --> Bluetooth > Pair new device
<p align="center">
<img width="20%" alt="Edited_20261126_144222" src="https://github.com/user-attachments/assets/bbff33ef-beac-4113-a46e-ed9a73cb362a" />
</p>

<!-- 
<img src="https://github.com/user-attachments/assets/263584ad-ffa5-4429-afc4-e1e5d176ebce" width="30%" alt="ble device">


https://github.com/user-attachments/assets/6a893ce2-07dc-420e-a74e-3e57f22fd450 -->

## Quick start
1. Set the DIP switches to the desired mode before powering the device.
2. Connect power using the USB Type-C cable.
3. Pair/connect to the BLE keyboard named **MorseBle**. The device waits for this connection before reading the DIP switches.
4. The device reads the DIP setting once during startup. To change modes later, set the switches and reboot/reset the device.
5. For Notepad mode, open Notepad and focus its text area during the five-second startup pause. The device then types its heading and is ready for Morse input.
6. For browser mode, open the target site, configure its keyer settings, join or start a session as needed, and keep that page focused. The site receives the key presses from the device.

>Only one host should be connected over Bluetooth at a time. Disconnect the current host before connecting another computer or phone.

## DIP switch modes

| DIP value | SW1 | SW2 | SW3 | SW4 | SW5 | Selected mode | Key behavior / speed | Buzzer|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 0 | 0 | 0 | 0 | Notepad straight key | 10 WPM | ✅ | 
| 1 | 1 | 0 | 0 | 0 | 0 | Notepad paddle key | 12 WPM |  :white_check_mark: |
| 3 | 1 | 1 | 0 | 0 | 0 | VBand Type 1 | Configurable on the website | :x: |
| 7 | 1 | 1 | 1 | 0 | 0 | VBand Type 2 | Configurable on the website | :x: |
| 15 | 1 | 1 | 1 | 1 | 0 | VBand Type 3 | Configurable on the website | :x: |
| 31 | 1 | 1 | 1 | 1 | 1 | VBand Type 4 | Configurable on the website | :x: |


>Buzzer and LEDs follow the generated Morse elements.

## Browser tools

These are the browser destinations and key modes recorded for the project. Configure Morse key type and WPM in each site's settings where available. Keep the browser page focused while sending.

| Website | Straight key | Paddle | Mode |
|:---:|:---:|:---:|:---:|
| [VBand](https://hamradio.solutions/vband/) | Yes | Yes | Type 1 |
| [Vail](https://vail.woozle.org/) | Yes | Yes | Type 2 |
| [Vail Morse](https://vailmorse.com/) | Yes | Yes | Type 2 |
| [Morse Me Please](https://morsemeplease.com/) | :x: | Yes | Type 3 |
| [CW Bot](https://cw-bot.hamradioduo.com/) | Yes | Yes | Type 1 |
| [CW Checker](https://tools.hamradioduo.com/cw-checker/) | Yes | Yes | Type 1 |
| [Morse Code World keyer](https://morsecode.world/international/trainer/keyer.html) | Yes | Yes | Type 4 |
| [Morse Halb](https://morse.halb.it/) | Yes | Yes | Type 3 |
| [CW Open Shack chat](https://cw.openshack.com/cwchat/) | Yes | Yes | Type 4 |

## Android apps

Configure the key type and WPM in the app where those options are available.

| App | Straight key | Paddle | Mode |
|:---:|:---:|:---:|:---:|
| [Morse](https://play.google.com/store/apps/details?id=com.mweutbycjynwq.morse&hl=en_IN) | Yes | No | Type 1 |
| [Morse Keyer](https://play.google.com/store/apps/details?id=com.qft8.morsekeyer&hl=en_IN) | Yes | Yes | Type 1 |
| [Morse Chat](https://play.google.com/store/apps/details?id=digital.dong.morsechat&hl=en_IN) | Yes | No | Type 1 |





## Firmware Bin file

Bin file and instructions to upload will be added soon!! .

## Notes

- The mode is selected once after BLE connects. Reboot after changing DIP switches.
- Disconnect one computer/phone before pairing the adapter with another host.
- Slight warmth during BLE operation has been observed on the prototype.


📫 Mail for any query/support:
   rn.ksheer+vband@gmail.com

