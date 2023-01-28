# Project Start

I had some fun and also some frustrations along the way with this project-starting very simple with the breadboard, I realized that a single breadboard, at least the ones I was used to working with, was not wide enough so I had to connect a pair of them together and have the ESP straddle the both of them in order to gain access to both sides of the ESP32 pin headers for breadboard wiring:

![Breadboard Beginnings](images/breadboard-beginnings.jpg)

# Adopt/Install/or otherwise... Get Your ESP into ESPHome

Now that my ESP32 had pins and wasn't dangling on the end of a hanging USB cable, I did the install of the code, this isn't too difficult and there are many guides and several ways to do this using ESPHome either inside HA as an add-on, or by installing the tools on your PC. You may need to install a com port driver which is available on the esphome.io website my pc alread had these drivers as I had used some other random USB-COM port device and many of them share the same chipset.

# Connecting sensors...

The first connections I made were for the BME280 (Press/Humid/Temp) sensor which wasn't too hard, basically you chose pins on the ESP32 for the I2C bus, one being clock and other data (on the BME280 side it's SCK and SD1) and then wire it up! sounds easy right??? I realized the code sample I used wasn't for the BME280 but Rather some other environment sensor that looks similar but operates on another address but after a little bit I figured this out and my sensor started to come alive!
