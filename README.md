
#include <LiquidCrystal.h>
const int n=215;
const int trigPin=6;
const int echoPin=7;
long duration;
int distance;
int x;
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
   pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
  lcd.begin(16, 2);
  lcd.println(distance);
}

void loop() {
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

duration=pulseIn(echoPin, HIGH);
distance=duration*0.034/2;
x=n-distance;
Serial.print("Height:");
Serial.println(x);
  lcd.setCursor(0, 1);
  lcd.println(x);
}
