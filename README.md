#include <SoftwareSerial.h>

SoftwareSerial Bluetooth(8,9); // RX, TX

int relay1 = 2;
int relay2 = 3;
int relay3 = 4;
int relay4 = 5;


String readString;

void setup() {
  Serial.begin(9600);
  Bluetooth.begin(9600);
  pinMode(relay1, OUTPUT); 
  pinMode(relay2, OUTPUT); 
  pinMode(relay3, OUTPUT); 
  pinMode(relay4, OUTPUT); 
 
}

void loop() {
  while (Bluetooth.available()) {
    delay(3);  
    char c = Bluetooth.read();
    readString += c; 
  }
    readString.toLowerCase();
  if (readString.length() >0) {
    Serial.println(readString);
    if (readString == "*light on#")     
    {
      digitalWrite(relay1, HIGH);
    }
  else if (readString == "*light off#")
    {
      digitalWrite(relay1, LOW);
    }
    //relay2
   else if (readString == "*fan on#")     
    {
      digitalWrite(relay2, HIGH);
    }
   else if (readString == "*fan off#")
    {
      digitalWrite(relay2, LOW);
    }
    //relay3    
    else if (readString == "*source on#")     
    {
      digitalWrite(relay3, HIGH);
    }
     else if (readString == "*source off#")
    {
      digitalWrite(relay3, LOW);
    }
    //relay4    
    else if (readString == "*switch on#")     
    {
      digitalWrite(relay4, HIGH);
    }
   else if (readString == "*switch off#")
    {
      digitalWrite(relay4, LOW);
    }
    //All on / off    
    else if (readString == "*all on#")     
    {
      digitalWrite(relay1, HIGH);
      digitalWrite(relay2, HIGH);
      digitalWrite(relay3, HIGH);
      digitalWrite(relay4, HIGH);
     
    }
    else if (readString == "*all off#")
    {
      digitalWrite(relay1, LOW);
      digitalWrite(relay2, LOW);
      digitalWrite(relay3, LOW);
      digitalWrite(relay4, LOW);
    }
    //next
    else {
    } 
  }
  readString="";
  } 
