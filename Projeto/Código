#include <Arduino.h>

#define echo 8
#define trigger 9

#define buzzer 13

#define R_led 12
#define Y_led 7
#define G_led 2

int flag = 0;
int distance_cm;

void setup()
{
  Serial.begin(9600);

  pinMode(echo, INPUT);
  pinMode(trigger, OUTPUT);

  pinMode(buzzer, OUTPUT);

  pinMode(R_led, OUTPUT);
  pinMode(Y_led, OUTPUT);
  pinMode(G_led, OUTPUT);
  delay(100);
}

void loop()
{

  digitalWrite(trigger, LOW);
  delayMicroseconds(2);
  digitalWrite(trigger, HIGH);
  delayMicroseconds(10);
  long time = pulseIn(echo, HIGH);
  distance_cm = time / 28.5 / 2;

  if (distance_cm < 10)
  {
    flag = !flag;
    digitalWrite(R_led, HIGH);
    digitalWrite(Y_led, LOW);
    digitalWrite(G_led, LOW);
  }

  else if (distance_cm >= 10 && distance_cm < 20)
  {
    flag = 0;
    digitalWrite(R_led, LOW);
    digitalWrite(Y_led, HIGH);
    digitalWrite(G_led, LOW);
  }

  else if (distance_cm >= 20 && distance_cm <= 30)
  {
    flag = 0;
    digitalWrite(R_led, LOW);
    digitalWrite(Y_led, LOW);
    digitalWrite(G_led, HIGH);
  }

  else
  {
    flag = 0;
    digitalWrite(R_led, LOW);
    digitalWrite(Y_led, LOW);
    digitalWrite(G_led, LOW);
  }

  digitalWrite(buzzer, flag);
  Serial.print("cm: ");
  Serial.println(distance_cm);
  delay(150);
}