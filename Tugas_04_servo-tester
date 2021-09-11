```ino
/* Tugas Praktikum 4
Membuat servo tester menggunakan potensiometer sebagai masukan 
G64180030 - Zahra Aulia Firdausi

Link drive video :
https://drive.google.com/file/d/1NqTiyST1PBW6KHooqGLXLDzoTpyeaTny/view?usp=sharing
*/


#include <Servo.h>

int potensioPin = 0; //deklarasi pin analog potensiometer yang terhubung dengan potensio meter = A0
int servoPin = 9; // deklarasi pin digital servo = 9

Servo servo;

void setup() {
    servo.attach(servoPin); // untuk mengontrol servo
}

void loop() {
    int reading = analogRead(potensioPin);  // membaca inputan dari potensiometer
    int angle = map(reading, 0, 1023, 0, 180); // untuk menyimpan sudut arus servo dalam derajat 0 - 180 derajat
    servo.write(angle); // output
}
```
