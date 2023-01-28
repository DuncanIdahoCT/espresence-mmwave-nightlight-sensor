# espresence-mmwave-nightlight-sensor
Making a hidden mmWave presence sensor that looks like it belongs in a nice bathroom or hallway!

![mmWave Nightlight Sensor](/static/images/finished%20product.jpg)

Assemnbly notes and images can be found here [here](static/project.md)!

# A bit of back-story...

When I first discovered the magic of mmWave presence sensors for home automation, I started tinkering with the help of various build guides and ESPHome yaml code examples and came up with this:

![mmWave basic sensor with enclosure](/static/images/small%20sensor%20enclosure.jpg)

These work great in not obvious locations such as atop appliances or cabinets:

![sensor placement 1](/static/images/sensor%20placement%201.jpg)
![sensor placement 2](/static/images/sensor%20placement%202.jpg)

So my first thought was to take what I already had working well and adapt it to a bathroom which is probably the most difficult room for most people who are looking to add presence sensors. I considered many options but none would work well or have even the most remote chance of being approved by my wife :) so I came up with what I personally thought was a fine idea:

![original idea](/static/images/original%20idea.jpg)

The thinking with the above was that the bathroom vanity outlets are higher up in the room than a normal wall outlet and also, at least for me, decently placed for room sensor field of view. And since I didn't want to block the outlets, I started with an outlet extender, of course I need 5v power so I chose one with USB and then I found these handy little USB swivels and since we have nightlights in our bathrooms, I added that on too... you can see where this is going! My idea was very promptly rejected and declared hideous looking! :/

Personally I thought it was great since I could angle the sensor box using the USB swivel and there were no visible wires plus a nightlight and no blocked outlet... triple-win. Nope!

So I set out to find something else, my next idea was to look for a smart outlet that had perhaps an ESP8266 module inside it for wifi, they do exist but these smart outlets tend to be super ugly and also very difficult to open up and also there are only a handful that are easy to hack using something like Tasmota so you can use them normally in ESPHome so I abandoned that idea.

Then it occured to me that since I needed a nightlight, maybe I could find one that also had USB so I could use the internal power supply that would include, and what I stumbled on was perfect! A nightlight, and outlet extender... which I wasn't even counting on, plus USB. Additionally it was nice and big with a roomy night light difusser/lens and only screwed together so taking it apart to modify didn't involve breaking plastic or trying to crack the glue so I ordered one and started to tinker.



### Installation:
 * Download these files and copy them (keeping their subfolder paths) into your Home Assistant config/esphome main folder:

   ```
   header/leapmmw_sensor.h
   
   packages/leapmmw_sensor.yml
   ```
 
 * In Home Assistant add-on, click ESPHome>open web gui and create a new device chosing the "continue" option and give it a name such as:

   ```
   espresence-mmwave-nightlight
   ```

* Click next and chose the type of ESP module you used in your build, this isn't a critical thing to have match but as long as it's some kind of ESP32 you can just select that for now and click next.
* You'll see a new card appear in the background for your ESP device, this is just an empty shell with only basic initilization code so far... click skip because you don't want to install this basic code to the ESP quite yet.
* Now click edit on your new sensor in ESPHome and you'll see the basic code:
   ```
   esphome:
    name: espresence-mmwave-nightlight

   esp32:
    board: esp32dev
    framework:
      type: arduino

   # Enable logging
   logger:

   # Enable Home Assistant API
   api:
     encryption:
       key: "cEEo6Dse5jSfuJ2FznX+3n7A6+6ZmzVNe92axpm2t04="

   ota:
     password: "488d6a3de442afaddb0250cffce64711"

   wifi:
    ssid: !secret wifi_ssid
    password: !secret wifi_password

     # Enable fallback hotspot (captive portal) in case wifi connection fails
    ap:
      ssid: "Your-New-Esp-Multi-Sensor"
     password: "RvZXGuhrPCzl"

   captive_portal:
   ```

* The esisest way to proceed is to copy all the code above out to notepad++ or your favorite editor and then paste back in the entire code from:
   ```
   espresence-mmwave-nightlight-sensor.yaml
   ```
* Now just copy some key lines you saved from your new basic config and paste them into the relevant sections of the full config:

   ```
   substitutions:
      # change device name to match your desired name
      device_name: espresence-mmwave-nightlight
      # change sensor name below to the one you want to see in Home Assistant
      device_name_pretty: Bathroom Nightlight mmWave Occupancy Sensor
      # change room name below to the one you want to see in Home Assistant
      room: "Bathroom"
   ```
* The room: "name" is key as it will be the name of each sensor object in HA so if you chose "Office" here, you sensors will be Office Motion, Office Tempurature, etc...

* You'll also want to copy the generated api encryption key and ota password into this section of the full code:

   ```
   # Enable Home Assistant API
   api:
      encryption:
         key: "assigned_when_you_add_to_esphome"

   ota:
      password: "assigned_when_you_add_to_esphome"
   ```

* Lastly, in the wifi: section, there is a line that says "use_address: XXX.XXX.XXX.XXX" this is an optional element to workaround typical issues with mDNS and wifi/subnets. Basically if you find your device is always showing as offline in ESPHome or has any issues at all when making changes or updating OTA, you'll want this setting. Note: this is not a static IP, it just tells ESPHome to use an IP address to do all OTA work with a given ESP device. You can of course set a static IP but this isn't that. You'll also notice that the wifi ssid and passwords are variables, you'll also see at the top of the full config are references to "secrets" file. You'll need to create one or update the one in this repo and copy it to the config/esphom main folder... if you have setup other esp devices, changes are you have this already.

   ```
   # Connect to WiFi & create captive portal and web server
   wifi:
      ssid: "${ssid}"
      password: "${wifi_password}"
      use_address: XXX.XXX.XXX.XXX
   ```
# Comments are welcome

I've only created a few projects here now, so I'm happy to hear any suggestions.
