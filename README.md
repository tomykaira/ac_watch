Note: I developed on macOS. Please use corresponding commands for other OSes.

# Parts

- ESP32
  - MCU NodeMCU-32S
  - https://www.amazon.co.jp/gp/product/B078WM1YQW/ref=ppx_yo_dt_b_asin_title_o00__o00_s00?ie=UTF8&psc=1
  - any other arduino compatible ESP32 MCUs will work.
- AC Current sensor
  - TDK CCT261631-30-06-00
  - https://www.mouser.com/ProductDetail/TDK/CCT261631-30-06-00?qs=P9Xy8ZBwTyvObwTEyAtcGA==
  - Other sensors will work, but take care for voltage and current capacity.
- Some breadboard
- Some 10K resistor
- Jumpers

# Setup

Copy `ac.ino.sample` to `ac.ino` and configure it for IFTTT notification.

- ssid: your wifi SSID.
- password: your wifi password.
- webhook: your webhook URL. Get it from https://ifttt.com/maker_webhooks .

Install board manager and serial chip driver.

Arduino board manager
https://github.com/espressif/arduino-esp32/blob/master/docs/arduino-ide/boards_manager.md

CP2102 driver
https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers

Write the ac.ino to the board (change board name if you use different MCU dev boards).

```
/Applications/Arduino.app/Contents/MacOS/Arduino --upload --board "esp32:esp32:nodemcu-32s" --port /dev/cu.SLAB_USBtoUART -v ac.ino
```

# Wiring

- Connect two output pins of current sensor to the breadboard.
- Put 10K Ohm resister between them.
- Connect one pin to GND pin of MCU.
- Connect the other pin to A0 of MCU (in my case, 3rd pin of the left side, check pinouts in links below).
- Put the sensor around AC cable of the electric appliance you want to watch.
  - If the cable is paired, split by cutter and put the sensor to only one of the lines.

# Links

IFTTT webhooks
https://ifttt.com/maker_webhooks

Arduino board manager
https://github.com/espressif/arduino-esp32/blob/master/docs/arduino-ide/boards_manager.md

CP2102 driver
https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers

Pinouts
https://qiita.com/keitasumiya/items/5b4961de169299e902db

# Thanks

Kitsune san for the great idea.
