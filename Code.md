# Home-Automation-using-TSOP-Sensor
Home Automation using TSOP sensor

Code:
#include <IRremote.h>
int IRpin = 11;
IRrecv irrecv(IRpin);
decode_results results;
int Relay1=3; // Initializing the pins for Relay
int Relay2=4;
int Relay3=5;
int val1=0; // Inializing the variable for storing the last status of Relay_pins
int val2=0;
int val3=0;
void setup()
{
  Serial.begin(9600);
  irrecv.enableIRIn(); // Start the receiver
  pinMode(Relay1,OUTPUT);
  pinMode(Relay2,OUTPUT);
  pinMode(Relay3,OUTPUT);
  digitalWrite(Relay1,HIGH);
  digitalWrite(Relay2,HIGH);
  digitalWrite(Relay3,HIGH);
} 
void loop() 
{
  if (irrecv.decode(&results)) 
  {
   Serial.println(results.value); 
   delay(10); 
   irrecv.resume(); // Receive the next value
  }
  if(results.value==1086300255)
  {
    val1=digitalRead(Relay1);
    if(val1==0)
    {
      digitalWrite(Relay1,HIGH);
      val1=1;
      delay(100);
    }
    else
    {
      digitalWrite(Relay1,LOW);
      val1=0;
      delay(100);
    }
  }
  if(results.value==1086259965)
  {
    val1=digitalRead(Relay2);
    if(val2==0)
    {
      digitalWrite(Relay2,HIGH);
      val2=1;
      delay(100);
    }
    else
    {
      digitalWrite(Relay2,LOW);
      val2=0;
      delay(100);
    }
  }
  if(results.value==1086320655)
  {
    val1=digitalRead(Relay3);
    if(val3==0)
    {
      digitalWrite(Relay3,HIGH);
      val3=1;
      delay(100);
    }
  else
  {
    digitalWrite(Relay3,LOW);
    val3=0;
    delay(100);
  }
 if(results.value==1086268125)
 {
 }}
