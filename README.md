<h1 align="center">🛠 &nbsp; Automação residencial 🛠 &nbsp;</h1>
O objetivo principal deste projeto é desenvolver um sistema de automação residencial utilizando uma placa Arduino com Bluetooth sendo controlado remotamente por qualquer smartphone com sistema operacional Android. 
Para isso, um módulo Bluetooth é interfaceado com a placa Arduino na extremidade do receptor enquanto na extremidade do transmissor, uma aplicação GUI no telefone celular envia comandos ON/OFF para o receptor onde as cargas estão conectadas. Ao tocar no local especificado na GUI, as cargas podem ser LIGADAS/DESLIGADAS remotamente através desta tecnologia.

A demonstração do projeto está no vídeo do youtube abaixo:

<a href = "https://www.youtube.com/watch?v=1ieyT6df8ec" ><img src="https://github.com/aagarwal1012/Home-Automation/blob/master/Images/youtube_image.png" width="50%" /></a>  

Contents
--------
This Readme is divided into several parts
1. [Description](#description)
2. [Components](#components)
3. [Implementation](#implementation)


<a name="description">Description</a>
---------
This project is one of the important <a href = "https://www.projectsof8051.com/arduino-projects/">Arduino Projects</a>. Arduino based home automation using Bluetooth project helps the user to control any electronic device using Device Control app on their Android Smartphone. The android app sends commands to the controller – Arduino, through wireless communication, namely, Bluetooth. The Arduino is connected to the main PCB which has five relays as shown in the block diagram. These relays can be connected to different electronic devices like lights, television, fan, etc.  
When the user presses on the ‘On’ button displayed on the app for the device 1, the Buzzer is switched on. This Buzzer can be switched off, by pressing the same button again.  
Similarly, when the user presses on the ‘On’ button displayed on the app for the device 2, the fan is switched on. The fan can be switched off, by pressing the same button again.  
This project of home automation using Bluetooth and Arduino can be used for controlling any AC or DC devices.  
Given below is the flow diagram that explains the flow of the project.

<img src = "https://github.com/aagarwal1012/Home-Automation/blob/master/Images/diagram.jpg" width = "75%"/>  


<a name="components">Components</a>
---------
This section enlists various hardware and software componets used in the project.

#### Hardware
The list of components mentioned here are specifically for controlling 4 different loads.

- Arduino UNO
- HC – 05 Bluetooth Module
- 5 V Relay X 4
- Prototyping board (Bread board)
- Connecting wires
- Smartphone or tablet (Bluetooth enabled)
- 5V Power Source

#### Software

- Arduino 1.8.5 compiler
- [Android application](#app)



<a name="implementation">Implementation</a>
---------
### Circuit Diagram  

<img src = "https://github.com/aagarwal1012/Home-Automation/blob/master/Images/ciruit_diagram.png" width = "75%"/>  

### Arduino Code 

```
//Arduino uno
//by: Caio Rocha and Lucas Feitosa
 
#include <SPI.h>
#include <Ethernet.h>
#include <SoftwareSerial.h>

SoftwareSerial bluetooth(10, 11);
String readString;
 
int pino_rele1 = 3;
int pino_rele2 = 4;
int pino_rele3 = 5;
int pino_rele4 = 6;
boolean ligado = true;
boolean ligado_2 = true;
int incomingByte; 

void setup()
{
  Serial.begin(9600);
  bluetooth.begin(9600);
  pinMode(pino_rele1, OUTPUT);
  pinMode(pino_rele2, OUTPUT);
  pinMode(pino_rele3, OUTPUT);
  pinMode(pino_rele4, OUTPUT);
}
 
void loop()
{
  //Serial.println("LOOP");
  if (bluetooth.available() > 0) 
  {
    // read the oldest byte in the serial buffer:
    incomingByte = bluetooth.read();
    Serial.println(incomingByte);
    Serial.println("");
    // if it's a capital H (ASCII 72), turn on the LED:
    if (incomingByte == 49) 
    {
      digitalWrite(pino_rele1, LOW);
      bluetooth.println("LAMPADA 1: ON");
       
    }
    // if it's an L (ASCII 76) turn off the LED:
    if (incomingByte == 65) 
    {

     digitalWrite(pino_rele1, HIGH);
      bluetooth.println("LAMPADA 1: OFF");
      
    }
    if (incomingByte == 50) 
    {
      digitalWrite(pino_rele2, LOW);
      bluetooth.println("LAMPADA 2: ON");
       
    }
    // if it's an L (ASCII 76) turn off the LED:
    if (incomingByte == 66) 
    {

     digitalWrite(pino_rele2, HIGH);
      bluetooth.println("LAMPADA 2: OFF");
      
    }
    if (incomingByte == 51) 
    {
      digitalWrite(pino_rele3, LOW);
      bluetooth.println("LAMPADA 3: ON");
      
    }
    // if it's an L (ASCII 76) turn off the LED:
    if (incomingByte == 67) 
    {

     digitalWrite(pino_rele3, HIGH);
      bluetooth.println("LAMPADA 3: OFF");
      
    }
    if (incomingByte == 52) 
    {
      digitalWrite(pino_rele4, LOW);
      bluetooth.println("LAMPADA 4: ON");
       
    }
    // if it's an L (ASCII 76) turn off the LED:
    if (incomingByte == 68) 
    {

     digitalWrite(pino_rele4, HIGH);
      bluetooth.println("LAMPADA 4: OFF");
     
    }
    if (incomingByte == 57) 
    {

     digitalWrite(pino_rele1, LOW);
     digitalWrite(pino_rele2, LOW);
     digitalWrite(pino_rele3, LOW);
     digitalWrite(pino_rele4, LOW);
      bluetooth.println("TODAS AS LAMPADAS: ON");
     
    }

    if (incomingByte == 73) 
    {
      digitalWrite(pino_rele1, HIGH);
      digitalWrite(pino_rele2, HIGH);
      digitalWrite(pino_rele3, HIGH);
     digitalWrite(pino_rele4, HIGH);
      bluetooth.println("TODAS AS LAMPADAS: OFF");
     
    }
  
  } 
}
```


### Android App  

<img src = "https://github.com/aagarwal1012/Home-Automation/blob/master/Images/app_screenshot.png" width = "300"/>


Any suggestion are welcomed and feel free to open an <a href = "https://github.com/aagarwal1012/Home-Automation/issues">issue</a>.
