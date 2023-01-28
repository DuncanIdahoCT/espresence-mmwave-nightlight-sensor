# espresence-mmwave-nightlight-sensor
Making a hidden mmWave presence sensor that looks like it belongs in a nice bathroom or hallway!

![mmWave Nightlight Sensor](/static/images/finished%20product.jpg)

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

Then it occured to me that since I needed a nightlight, maybe I could find one that also had USB so I could use the internal power supply that would include, and what I stumbled on was perfect! A nightlight, and outlet extender... which I wasn't even counting on, plus USB. Additionally it was nice and big with a roomy night light difusser/lens and only screwed together so taking it apart to modify didn't involve breaking plastic or trying to crack the glue so I ordered one, or four I very rarely dip a toe in, tending more to deep dive lol.

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
