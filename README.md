This is a fork of the original project, support them [here](https://www.buymeacoffee.com/adonno):

# ESP32 Tag Reader for Home Assistant 

The tag reader is a simple to build/use NFC tag reader, specially created for [Home Assistant](https://www.home-assistant.io). It uses an ESP32 and the PN532 NFC module. The firmware is built using [ESPhome](https://www.esphome.io).


## Building the tag reader

To build your own tag reader, you need the following components:

 - [ESP32](https://www.amazon.com/dp/B0B19KRPRC?psc=1&ref=ppx_yo2ov_dt_b_product_details)  
 - [PN532 NFC Reader](https://www.amazon.com/dp/B01I1J17LC?psc=1&ref=ppx_yo2ov_dt_b_product_details)
 - [WS2812](https://s.click.aliexpress.com/e/_d82GRqr)
 - [Buzzer](https://s.click.aliexpress.com/e/_dZ5F5yj)

<!-- TODO upate tag case - this is different from the D1 mini now -->
The 3D models for the case are [here](https://www.thingiverse.com/thing:2472725). 

`Note`: I had to print this at 105% to get the proper fit. Your mileage may vary.


### Connecting the components
<!-- TODO update schematics - this is different from the D1 mini now -->
There are not too many components to connect, but it does require soldering. You will need the following:

- [Solder](https://s.click.aliexpress.com/e/_dT3S62j)
- [Soldering iron with a fairly thin tip](https://s.click.aliexpress.com/e/_dXaI6nz)
- [About 40cm of thin wire (at least 5 different colors)](https://s.click.aliexpress.com/e/_dZvoYoB)


Also, make sure that you have set the switches on the PN532 to the following:
- Switch 1: On (up)
- Switch 2: Off (down)

This enables the PN532 module to communicate with the ESP32 over I2C, and is required for the modules to work together!

To flash the reader firmware to your ESP32 you point ESPHome at [tagreader.yaml](tagreader.yaml).  
> :warning: The tag reader requires ESPHome `1.16.0` or later.

If you're new to ESPHome, we recommend that you use the [ESPHome Home Assistant add-on](https://esphome.io/guides/getting_started_hassio.html).



## Configuring for use with Home Assistant

The tag reader requires [Home Assistant](https://www.home-assistant.io) 0.115 or later.

If the tag reader is unable to connect to a wifi network, it will start a WiFi access point with a captive portal to allow you to enter your WiFi credentials.

The tag reader will be automatically discovered by Home Assistant once the tag reader is connected to the same network. You can follow the instructions in the UI to set it up.

## Usage

Scanned tags can be managed from the tags interface in Home Assistant. You can find it under config -> tags.

![Screenshot of the Home Assistant tag UI](docs/tag-ui.gif)
