## The Oscar Project
![Photos of Oscar](https://github.com/dhruv-kurpad/OscarProject-docs/blob/main/OscarGIF.gif "Some of my favorite photos of Oscar")
I started the [Oscar project](https://github.com/dhruv-kurpad/oscarProject) with the goal of being notified when my dog was having a seizure. Osacr was a [English Cream Golden Retriever](https://www.loveyourdog.com/english-cream-retriever/) who had a great life! Over the last 6 months Oscar started having seizures that continued to get more frequent and intense. As we were often out of the house, I was concerned that Oscar might have a seizure when none was around to help him. test

I wanted to build an app that could notify me if Oscar was having a seizure so I could head home and check on him if he was alone.

## Planning
With the idea of building an app that could identify a seizure and notify me I started looking for ways to build it. In the summer before my junior year, I had built a RC Car from scratch following the awesome tutorials from [Dronebot Workshop](https://dronebotworkshop.com/nrf24l01-wireless-joystick/). 

I knew I needed to build a sensor that could detect the movements of a seizure and notify me, I also had ideas about using a GPS to notify me if Oscar ever wandered off to the neighbors yards looking for treats. With these ideas I started thinking about  what my prototype would look like.

### Choosing the Microcontroller

While I had used an Arduino Uno for the car and Arduino Nano for the remote on the previous project, I knew I needed a microcontroller that was more capable than the Arduino, I needed something that could handle multiple sensors and could coneect to Wifi. I landed on the [ESP32](https://www.espressif.com/en/products/socs/esp32) because it had all the features I was looking for:
1. Low cost ([The ESP32 devkit on Amazon](https://amzn.to/3D02wyb) is $10.99 )
2. The ESP32 has integrated Wifi and Bluetooth, but I only plan on using the Wifi for now. But the Bluetooth could come handy for setup.
3. Power consumption, the ESP32 can be put into low power consumption mode for times when I was home to save battery
4. The ESP32 has dual cores so I can collect inputs from the different sensors at varying frequencies and still communicate over Wifi without worrying too much about the controller slowing things down.
5. Finally the ESP32 is much faster processor, [over 10 times faster](https://diyi0t.com/technical-datasheet-microcontroller-comparison/) than a Arduino. Making it possible for me to gt sensor readings more frequently.

### Sensors

1. [Accelerometer & Gyroscope](https://amzn.to/3skE855) For the sensors, I obviously needed a Accelerometer and Gyroscope. I settled on the [MPU6050](https://amzn.to/3skE855) primarily because it was not too expensive and I found a number of tutorials online on using it. The MPU6050's purpose was to detect rapid changes in Oscar's orientation while he was on his side(his seizures almost always involved him falling down and thrashing around while on his side)

2. [Pulse Sensor](https://amzn.to/3xKbThz) It turned out that the pulse sensor does not work well when connected to a dog vest. Abandoned the idea, bt still looking for a good way to get the pulse reading. I can see that he's panting before, during and after a seizure.

3. [GPS Sensor](https://amzn.to/3skeQnO) Added the Neo-6M GPS module to the mix to see if I could geocode his location and notify myself if he ever wandered out of the yard.

### Other Items

1. [Prototype board](https://amzn.to/2UjII79) to minify the sensor components when done.
2. [Connecting Wires](https://amzn.to/3CUrr6e) to connect and solder the components
3. Soldering iron
4. Hot glue gun 
5. Battery. Rather than try and provide a 3.3V input to the circuit, I am currently using 5V input, the converter to 3.3V is coming in a future version!

### Connections
For the initial prototype I only have the MPU6050 connected. Here's the wiring diagram 
![Connections](https://imgs/connections.png)
![Oscar wearing first prototype](https://github.com/dhruv-kurpad/OscarProject-docs/blob/main/Screenshot%20(1).png)
1. MPU6050


### Sensor Code
 
Sampleing rate (10/sec)
Frequency (10 sec with a pause of 30 sec)
Using multiple cores (1 for Wifi and sending data one for sensor)

#### Cloud Environment


