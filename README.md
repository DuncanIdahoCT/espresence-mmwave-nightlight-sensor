# espresence-mmwave-nightlight-sensor
Making a hidden mmWave presence sensor that looks like it belongs in a nice bathroom or hallway!

![mmWave Nightlight Sensor](/static/images/finished%20product.jpg)

When I first discovered the magic of mmWave presence sensors for home automation, I started tinkering with the help of various build guides and ESPHome yaml code examples and came up with this:

![mmWave basic sensor with enclosure](/static/images/small%20sensor%20enclosure.jpg)

These work great in not obvious locations such as atop appliances or cabinets:

![sensor placement 1](/static/images/sensor%20placement%201.jpg)
![sensor placement 2](/static/images/sensor%20placement%202.jpg)

### Installation:
 * Download these files and copy them (keeping their subfolder paths) into your Home Assistant config/esphome main folder:

   ```
   header/leapmmw_sensor.h
   
   packages/leapmmw_sensor.yml
   ```
 
 * In Home Assistant add-on, click ESPHome>open web gui and create a new device chosing the "continue" option and give it a name such as:

   ```
   espresence-office-multi-sensor
   ```

* Click next and chose the type of ESP module you used in your build, this isn't a critical thing to have match but as long as it's some kind of ESP32 you can just select that for now and click next.
* You'll see a new card appear in the background for your ESP device, this is just an empty shell with only basic initilization code so far... click skip because you don't want to install this basic code to the ESP quite yet.
