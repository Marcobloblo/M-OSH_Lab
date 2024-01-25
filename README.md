**Main objective**
Through the Microcontroller & Open-Source Hardware UF, we aim to understand how an IoT system works from all points of view.

This UF was organized around several points:
Firstly, the class was able to follow a course that teaches how to create a sensor (AIME internship), unfortunately our group couldn't attend as we're on a professionalization contract.
Secondly, we learned how to use a sensor with a microcontroller designed for this purpose (cf. practical work with Arduino), with several types of sensor, from touch screens to simple potentiometers.
Thirdly, we learned how to solder an electronic board with tin and pins to make it usable later on.
We then worked on an IoT/network part with software (Node Red), to enable communication between our system and a cloud database.
Finally, we designed the final electronic board on KiCad that could do everything we need to make a system that should detect a gas while sending the information to a cloud.

Github content:
On this repository you can find: 
- The Kicad project file with the electronic schematic and the routed PCB
- The Arduino code for our sensor
- The gas sensor datasheet
- The amplifier code on LTSpice
- The README file (you're reading it now 😊 )

Materials used in this project :
To carry out this project, we need :
- An Arduino UNO microcontroller, which will do all the calculations and into which we'll integrate our code.
- A LoRa module to transmit the data collected by the sensor
- A gas sensor designed during the AIME internship.

Once assembled, the project looks like this:
