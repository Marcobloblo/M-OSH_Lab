# Main Objective
Through the Microcontroller & Open-Source Hardware UF, we aim to understand how an IoT system works from all points of view.

This UF was organized around several points:
Firstly, the class was able to follow a course that teaches how to create a sensor (AIME internship), unfortunately our group couldn't attend as we're on a professionalization contract.
Secondly, we learned how to use a sensor with a microcontroller designed for this purpose (cf. practical work with Arduino), with several types of sensor, from touch screens to simple potentiometers.
Thirdly, we learned how to solder an electronic board with tin and pins to make it usable later on.
We then worked on an IoT/network part with software (Node Red), to enable communication between our system and a cloud database.
Finally, we designed the final electronic board on KiCad that could do everything we need to make a system that should detect a gas while sending the information to a cloud.

# Github content:
On this repository you can find: 
- The Kicad project file with the electronic schematic and the routed PCB
- The Arduino code for our sensor
- The gas sensor datasheet
- The amplifier code on LTSpice
- The README file (you're reading it now 😊 )

# Materials used in this project :
To carry out this project, we need :
- An Arduino UNO microcontroller, which will do all the calculations and into which we'll integrate our code.
- A LoRa module to transmit the data collected by the sensor
- A gas sensor designed during the AIME internship.

Once assembled, the project looks like this:

The Arduino code that makes it all work can be found in the git repository!
Here's the Node Red that receives the data and displays it on a web-accessible dashboard:

(img/)

#Kicad/Gaz Sensor part
The aim of this part is to create an intelligent sensor capable of detecting the presence of gas.

KiCad IMAGE

As far as the sensor is concerned, operation is relatively straightforward. Depending on whether a gas is present or not, and on the gas itself, the resistance of the sensor in the electronic circuit will vary. To be able to determine this, we need to amplify the output voltage to be able to measure it and do post-measurement processing.
In addition to the amplifier, we had to install 3 filters with different cut-off frequencies. Each filter has a purpose, to make the signal cleaner and more usable.
Thanks to all this circuitry, depending on the output voltage, we can deduce a different resistance value, which we code on 10 bits (2^10 values, i.e. 1024).

As far as the sensor is concerned, operation is relatively straightforward. Depending on whether a gas is present or not, and on the gas itself, the resistance of the sensor in the electronic circuit will vary. In order to determine this, we need to amplify the output voltage for measurement and post-measurement processing.
In addition to the amplifier, we had to install 3 filters with different cut-off frequencies. Each filter has a purpose, to make the signal cleaner and more usable.
Thanks to all this circuitry, depending on the output voltage, we can deduce a different resistance value, which we code on 10 bits (2^10 values, i.e. 1024).

PCB IMAGE

#Conclusion
At the end of this project, we were able to grasp all the concepts associated with an IoT system, from the physical part to the creation of the sensor, from the electronic part with the soldering and routing of the PCB and the creation of the electronic model on KiCad, to the communication and protocol part with the configuration via Arduino of the LoRa module.
