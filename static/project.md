# Opening up and modifying the first model I got from Amazon

As mentioned, the unit is simply screwed together and inside its quite spacious so adding the ESP8266 and mmWave sensor was easy. I used the stacked header pins as the method of attachment and sandwitched the internal nightlight reflector between them:

![prototype internals 1](/static/images/prototype%20internals%202.jpg)
![prototype internals 1](/static/images/prototype%20internals%203.jpg)
![prototype internals 1](/static/images/prototype%20internals%204.jpg)

This worked well for my prototype except for one minor issue which was a single tall capacitor was obstructing things when I tried to reassemble so I simple de-soldered it and replaced it laid over using some angled breakaway header pins, no sweat:

![laying over a cap](/static/images/laying%20over%20a%20cap.jpg)

For the prototype I tapped into the 5v right at the USB header which might have seemed obvious but wasn't the easiest place to work and the garbage wire I used made it even more annoying but after some swearing, I got it done:

![prototype internals 1](/static/images/prototype%20internals%205.jpg)


These work great in not obvious locations such as atop appliances or cabinets:

![sensor placement 1](/static/images/sensor%20placement%201.jpg)
![sensor placement 2](/static/images/sensor%20placement%202.jpg)

So my first thought was to take what I already had working well and adapt it to a bathroom which is probably the most difficult room for most people who are looking to add presence sensors. I considered many options but none would work well or have even the most remote chance of being approved by my wife :) so I came up with what I personally thought was a fine idea:




# Installation:
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
