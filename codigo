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
