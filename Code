#include <Servo.h>
Servo myServo;
const int line = 5;
const int led = 7;
const int btn = A1;
const int buzz = 6;
const int soundPin = A0;
const int trig = 10;
const int echo = 9;
const int In1 = 4;
const int In2 = 2;
const int EnA = 3;
 
void setup() {
  Serial.begin(9600);
  pinMode(line, INPUT);
  pinMode(led, OUTPUT);
  pinMode(btn, INPUT);
  pinMode(buzz, OUTPUT);
  pinMode(soundPin, INPUT);
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
  pinMode(In1, OUTPUT);
  pinMode(In2, OUTPUT);
  pinMode(EnA, OUTPUT);
  myServo.attach(11);
}
 
void LED(){
  int val = digitalRead(line);
  if (val == 1){
    digitalWrite(led, HIGH);
  }
  else{
    digitalWrite(led, LOW);
  }
}
 
void BUZZ(){
  int push = digitalRead(btn);
  if(push == HIGH)
  {
    tone(buzz, 500, 200);
  }
  else
  {
    noTone(buzz);
  }
}
 
void SERVO(){
  Serial.println(analogRead(soundPin));
  int sound = analogRead(soundPin);
  if (sound > 10){
    myServo.write(180);
    delay(500);
  }
  else{
    myServo.write(0);
    delay(500);
  }
}
 
void MOTOR(){
  long duration, cm;
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(5);
  digitalWrite(trig, LOW);
  duration = pulseIn(echo, HIGH);
  cm = SoS(duration);
  digitalWrite(In1, HIGH);
  digitalWrite(In2, LOW);
  long delVal = map(cm, 5, 300, 70, 255);
  analogWrite(EnA, delVal);
  delay(500);
  digitalWrite(In1, LOW);
  digitalWrite(In2, LOW);
  delay(100);
}
 
long SoS(long pulse){
  return pulse / 29 / 2;
}
 
void loop() {
  LED();
  BUZZ();
  SERVO();
  MOTOR();
}
