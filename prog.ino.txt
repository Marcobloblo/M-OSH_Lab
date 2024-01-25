```arduino
#include <TheThingsMessage.h>
#include <TheThingsNetwork.h>
#include <SoftwareSerial.h>


#define debugSerial Serial
#define rxPin 3 //Broche 11 en tant que RX, � raccorder sur TX du HC-05
#define txPin 4 //Broche 10 en tant que RX, � raccorder sur TX du HC-05
#define baudrate 9600
#define debugSerial Serial
SoftwareSerial loraSerial(rxPin ,txPin); //D�finition du software serial

// Replace REPLACE_ME with TTN_FP_EU868 or TTN_FP_US915
#define freqPlan TTN_FP_EU868
int sensorPin=A0;
int sensorData;
float sensor_volt;
// Set your AppEUI and AppKey
const char *appEui = "c6eb805a5265f640";
const char *appKey = "fa864474515865f08ee5fa168079a411";



TheThingsNetwork ttn(loraSerial, debugSerial, freqPlan);

//devicedata_t data = api_DeviceData_init_default;
int gazData;

void setup()
{
  loraSerial.begin(57600);
  debugSerial.begin(9600);

  // Wait a maximum of 10s for Serial Monitor
  while (!debugSerial && millis() < 10000)
    ;

  debugSerial.println("-- STATUS");
  ttn.showStatus();

  debugSerial.println("-- JOIN");
  ttn.join(appEui, appKey);

  // Select what fields to include in the encoded message
  /*data.has_motion = true;
  data.has_water = false;
  data.has_temperature_celcius = true;
  data.has_temperature_fahrenheit = true;
  data.has_humidity = true;
*/
  pinMode(sensorPin,INPUT);


}

void loop()
{
  debugSerial.println("-- LOOP");

  // Read the sensors
  /* data.motion = true;
  data.water = 682;
  data.temperature_celcius = 30;
  data.temperature_fahrenheit = 86;
  data.humidity = 97;
*/
  // Encode the selected fields of the struct as bytes
  byte *buffer;
  size_t size;
  int gazData;
  sensorData = analogRead(sensorPin);       
 
  Serial.print("Sensor Data:");
  Serial.print(sensorData);
  sensor_volt = sensorData/1024*5.0;
  gazData = sensorData;
//  Serial.print(sensor_volt);
//  Serial.println("V");
//  Serial.print("sensor_volt = ");  
//  Serial.print(byte(gazData));
//  Serial.print("Sizeof GazData"); 
//  Serial.print(sizeof(gazData));
  byte tab[2];
  tab[0] = gazData&0xff;
  tab[1] = (gazData >> 8)&0xff;

  //TheThingsMessage::encodeDeviceData(&gazData, &buffer, &size);
  //TheThingsNetwork::sendBytes(&gazData,&buffer, &size);
  ttn.sendBytes(tab, 2);
  
  delay(10000);
}

``` c'est celui qui s'appelle cap_gaz_lora