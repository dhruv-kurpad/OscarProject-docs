## The Oscar Project

I started the [Oscar project](https://github.com/dhruv-kurpad/oscarProject) with the goal of being notified when my dog was having a seizure. Osacr was a [English Cream Golden Retriever](https://www.loveyourdog.com/english-cream-retriever/) who had a great life! Over the last 6 months Oscar started having seizures that continued to get more frequent and intense. As we were often out of the house, I was concerned that Oscar might have a seizure when none was around to help him. 

I wanted to build an app that could notify me if Oscar was having a seizure so I could head home and check on him if he was alone.

## Planning
With the idea of building an app that could identify a seizure and notify me I started looking for ways to build it. In the summer before my junior year, I had built a RC Car from scratch following the awesome tutorials from [Dronebot Workshop](https://dronebotworkshop.com/nrf24l01-wireless-joystick/). 

I knew I needed to build a sensor that could detect the movements of a seizure and notify me, I also had ideas about using a GPS to notify me if Oscar ever wandered off to the neighbors yards looking for treats. With these ideas I started thinking about  what my prototype would look like.

### Choosing the Microcontroller

While I had used an Arduino Uno for the car and Arduino Nano for the remote on the previous project, I knew I needed a microcontroller that was more capable than the Arduino, I needed something that could handle multiple sensors and could coneect to Wifi. I landed on the [ESP32](https://www.espressif.com/en/products/socs/esp32) because it had all the features I was looking for:
1. Low cost ([The ESP32 devkit on Amazon](https://amzn.to/3D02wyb) is $10.99 )
2. The ESP32 has integrated Wifi and Bluetooth, but I only plan on using the Wifi for now. But the Bluetooth ould come handy for setup.
3. Power consumption, the ESP32 can be put into low power consumption mode for times when I was home to save battery
4. The ESP32 has dual cores so I can collect inputs from the different sensors at varying frequencies and still communicate over Wifi without worrying too much about the controller slowing things down.
5. Finally the ESP32 is much faster processor, [over 10 times faster](https://diyi0t.com/technical-datasheet-microcontroller-comparison/) than a Arduino. Making it possible for me to gt sensor readings more frequently.

### Sensors

1. [Accelerometer & Gyroscope](https://amzn.to/3skE855) For the sensors, I obviously needed a Accelerometer and Gyroscope. I settled on the [MPU6050](https://amzn.to/3skE855) primarily because it was not too expensive and I found a number of tutorials online on using it.

