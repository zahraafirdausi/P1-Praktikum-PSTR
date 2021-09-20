/*
 * Tugas Praktikum 5 - Lampu Otomatis dengan Relay - 
 * menggunakan sensor ultra sonik
 * Zahra Aulia Firdausi
 * G64180030
 */

const int TRIG_PIN  = 7; // Deklarasi pin digital untuk pin TRIG sensor unltrasonik
const int ECHO_PIN  = 6; // Deklarasi pin digital untuk pin ECHO sensor unltrasonik
const int RELAY_PIN = 3; // Deklarasi pin connected to Relay's pin
const int DISTANCE_THRESHOLD = 50; // jarak threshold-nya = 50 centimeters
int pinled = 10; // deklarasi pin LED 

// variables durasi dan jarak
float duration_us, distance_cm;

void setup() {
  Serial.begin (9600);        // initialize serial port
  pinMode(TRIG_PIN, OUTPUT);  // set TRIG pin untuk output mode
  pinMode(ECHO_PIN, INPUT);   // set ECHO pin untuk input mode
  pinMode(RELAY_PIN, OUTPUT); // set RELAY pin untuk output mode
  pinMode(pinled, OUTPUT); // Set pin LED untuk output mode
}

void loop() {
  // generate 10-microsecond pulse to TRIG pin
  digitalWrite(TRIG_PIN, LOW); 
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, HIGH); 

  // measure duration of pulse from ECHO pin
  duration_us = pulseIn(ECHO_PIN, HIGH);
  
  // Perhitungan Jarak 
  distance_cm = 0.017 * duration_us;

  
  // kondisi apabila jarak yang diterima kurang dari 50 cm maka Relay pin akan menyala, dan Lampu LED hidup
  // begitu pun sebaliknya
  if(distance_cm < DISTANCE_THRESHOLD){
    digitalWrite(RELAY_PIN, LOW); // turn on Relay
    digitalWrite(pinled, HIGH);
  }
 
  else {
    digitalWrite(RELAY_PIN, HIGH);  // turn off Relay
    digitalWrite(pinled, LOW);
  }
  
  // print nilai jarak ke Serial Monitor
  Serial.print("distance: ");
  Serial.print(distance_cm);
  Serial.println(" cm");

  delay(500);
}
