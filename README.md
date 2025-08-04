#include <Servo.h>  
#include <keypad.h>
const int led = 13;  //sets up the led
const int buzz = 12; //sets up the buzzer
const int dist = 8;  //sets up the distance sensor
Servo myServo; //sets up the servo motor
const byte ROWS = 4; //there are four rows on the keypad
const byte COLS = 4; //there are four colums on the keypad

char hexaKeys[ROWS][COLS] = {
  {'1', '2', '3', 'A'},
  {'4', '5', '6', 'B'},
  {'7', '8', '9', 'C'},
  {'*', '0', '#', 'D'},
}; //explains to the system what each number on the keypad is

byte rowPins[ROWS] = {1, 2, 3, 4};
byte colPins[COLS] = {5, 6, 7, 9}; 
//explains what pins each button is connected to
Keypad customKeypad = Keypad(makeKeymap(hexaKeys), rowPins, colPins, ROWS, COLS); 
//impliments a feature from the library included in the beginning of the code that allows a user to interact with the system

void setup{
 pinMode(buzz,OUTPUT);
 pinMode(led,OUTPUT);
 pinMode(motor, OUTPUT);
 pinMODE(dist,INPUT);
 myServo.attach(9);
 Serialprint(angle(90));
 Serialbegin(9600);
} //sets up weather pins are meant to0 recieve a signal or produce a signal

void alarm{
  digitalRead(dist);
  if (dist <  90){
    digitalWrite(led,HIGH)
    tone(buzz,1500);
    delay(1000);
  }
}//this part of the code sets up what will happen if your to close to the distance sensor

void loop{
 const password = customKeypad.getKey('1' '4' '1' '5' '9'); //this is the password
 
  if(password){
    Serial.print(angle(90));
    analogWrite(alarm,LOW);
  }else{
    analogWrite(alarm,HIGH);
  }
}//this part of the code allows the alarm to be turned of if the password is typed
