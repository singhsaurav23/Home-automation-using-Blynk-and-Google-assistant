# Home-automation-using-Blynk-and-Google-assistant


Coding for Node MCU
/* 
 *  Coding is done in Arduino IDE 
 *  Node MCU library are added 
 *  Virtual pins are used for data transfer over Wi-Fi
 *  
 
*/
#define BLYNK_PRINT Serial
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

int a,b,c,d;


//GPIO Pin outs for Node MCU.
int sw1=16;
int sw2=5;
int sw3=4;
int sw4=0; 

//functions to accept data from Blynk App and Google assistant.
BLYNK_WRITE(V1){a=param.asInt();}
BLYNK_WRITE(V2){b=param.asInt();}
BLYNK_WRITE(V3){c=param.asInt();}
BLYNK_WRITE(V4){d=param.asInt();}



//Assignment of Indicators to virtual pin
WidgetLED ST1(V20);
WidgetLED ST2(V21);
WidgetLED ST3(V22);
WidgetLED ST4(V23);



// You should get Auth Token in the Blynk App.
// Go to the Project Settings (nut icon).
char auth[] = "jLWP2HTNC4kcQvNw037DJURV_cvWcJSl";
char ssid[] = "Redmi";
char pass[] = "Rohit321";

void setup()
{
  
  Serial.begin(9600);
  pinMode(sw1,OUTPUT);
  pinMode(sw2,OUTPUT);
  pinMode(sw3,OUTPUT);
  pinMode(sw4,OUTPUT);
  Blynk.begin(auth, ssid, pass);

}

void loop()
{
  Blynk.run();
  BLYNK_CONNECTED();
  BLYNK_WRITE(V1);
  BLYNK_WRITE(V2);
  BLYNK_WRITE(V3);
  BLYNK_WRITE(V4);

digitalWrite(sw1,a);
   if(a>0)
    ST1.off();
   else
    ST1.on(); 
  digitalWrite(sw2,b);
  if(b>0)
    ST2.off();
   else
    ST2.on(); 
  digitalWrite(sw3,c);
   if(c>0)
    ST3.off();
   else
    ST3.on();
  digitalWrite(sw4,d); 
   if(d>0)
    ST4.off();
   else
    ST4.on();
             
}








