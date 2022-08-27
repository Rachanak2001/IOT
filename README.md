# IOT

https://wokwi.com/projects/335586982610600531<br>
<br>
https://wokwi.com/projects/333715360946586195 :- Traffic led<br>
<br>
https://wokwi.com/projects/333801426044060243  :-RGB LED<br>
<br>
https://wokwi.com/projects/333805190238962259  :-RGB LED2<br>
<br>
https://wokwi.com/projects/322062421191557714  :-Hello wokwi<br>
<br>
https://wokwi.com/projects/334977593624232530 : servo motar <br>
<br>
https://wokwi.com/projects/334977593624232530  :-    servo motar using for loop<br>
<br>
https://wokwi.com/projects/334977602579071570 :-Servo motor with slide potentiometer<br>
<br>
https://wokwi.com/projects/334977602579071570 :-Servo motor with slide potentiometer<br>
<br>
https://wokwi.com/projects/335065707348755026 :-BUZZER<br>
<br>
https://wokwi.com/projects/335065844754154067 :-BUZZER with Push button<br>
<br>
https://wokwi.com/projects/335131064102027860 :-Ultrasonic<br>
<br>
https://wokwi.com/projects/335070139005272658 :-Ultrasonic sensor with buzzer<br>
<br>
https://wokwi.com/projects/335075055329346132 :-varring with intensity of Ultrasonic with buzzer<br>
<br>
https://wokwi.com/projects/335611619397599827 :-varring with distance using led<br>
<br>
https://wokwi.com/projects/335615459073196626 :-Two ultrasonic with buzzer and led.<br>
<br>
https://wokwi.com/projects/335701857976451668 :-Potentiometer with LED<br>
<br>
https://wokwi.com/projects/335702826545054292 :-Servo motor with pushbutton<br>
<br>

**LAB LIST**
1. https://wokwi.com/projects/338225981441442386 :-ESP32(LED/Buzzer)<br>
   https://wokwi.com/projects/338770823644971603 :-Arduino(LED/BUZZER)<br>
<br>
3. https://wokwi.com/projects/338147082096345683 :-DHT22 ( humidity sensor and temperature).<br>
<br>
5. https://wokwi.com/projects/338154081559249491 :-DHT22+LCD(humidity sensor and temperature)<br>
<br>
<br>
**HARDWARE**<br>
**IR SENSOR**<br>
int ir=D5;<br>
int led=D6;
void setup() {<br>
  // put your setup code here, to run once:<br>
  pinMode(ir,INPUT);<br>
    pinMode(led,OUTPUT);<br>
    Serial.begin(9600);<br>
    
}<br>

void loop() {<br>
  // put your main code here, to run repeatedly:<br>
  int irvalue=digitalRead(ir);<br>
  if(irvalue==LOW)<br>
  {<br>
    Serial.println("LOW");<br>
    digitalWrite(led,HIGH);<br>
  }<br>
  else<br>
  {<br>
    Serial.println("HIGH");<br>
    digitalWrite(led,LOW);<br>
  }<br>
delay(100);<br>
}<br>

![image](https://user-images.githubusercontent.com/97940850/182358111-4c419a1d-794c-43d8-b235-596bd407dbc6.png)<br>
<br>
**Chassing LED**<br>
int pinsCount=7;                        // declaring the integer variable pinsCount<br>
int pins[] = {D0,D1,D2,D3,D4,D5,D6};          // declaring the array pins[]<br>
 <br>
void setup() {                <br>
  for (int i=0; i<pinsCount; i=i+1){    // counting the variable i from 0 to 9<br>
    pinMode(pins[i], OUTPUT);            // initialising the pin at index i of the array of pins as OUTPUT<br>
  }<br>
}
 <br>
void loop() {<br>
  for (int i=0; i<pinsCount; i=i+1){    // chasing right<br>
    digitalWrite(pins[i], HIGH);         // switching the LED at index i on<br>
    delay(100);                          // stopping the program for 100 milliseconds<br>
    digitalWrite(pins[i], LOW);          // switching the LED at index i off<br>
  }<br>
 for (int i=pinsCount-1; i>0; i=i-1){   // chasing left (except the outer leds)<br>
   digitalWrite(pins[i], HIGH);         // switching the LED at index i on<br>
   delay(100);                          // stopping the program for 100 milliseconds<br>
  digitalWrite(pins[i], LOW);          // switching the LED at index i off<br>
  <br>
}<br>
}<br>
<br>
**flood monitoring using thingspeak:-**<br><br>
#include "ThingSpeak.h"<br>
#include <ESP8266WiFi.h><br>
const int trigPin1 = D6;<br>
const int echoPin1 = D7;<br>
#define redled D0<br>
#define grnled D1<br>
#define BUZZER D5 //buzzer pin
unsigned long ch_no = 1053193;//Replace with Thingspeak Channel number<br>
const char * write_api = "1WGTOHK9622G57JI";//Replace with Thingspeak write API<br>
char auth[] = "mwa0000027193727";<br>
char ssid[] = "SATHWIKA";<br>
char pass[] = "Mohitha96";<br>
unsigned long startMillis;<br>
unsigned long currentMillis;<br>
const unsigned long period = 10000;<br>
WiFiClient  client;<br>
long duration1;<br>
int distance1;<br>
void setup()
{<br>
  pinMode(trigPin1, OUTPUT);<br>
  pinMode(echoPin1, INPUT);<br>
  pinMode(redled, OUTPUT);<br>
  pinMode(grnled, OUTPUT);<br>
  digitalWrite(redled, LOW);<br>
  digitalWrite(grnled, LOW);<br>
  Serial.begin(115200);<br>
  WiFi.begin(ssid, pass);<br>
  while (WiFi.status() != WL_CONNECTED)<br>
  {<br>
    delay(1000);<br>
    Serial.print(".");<br>
  }<br>
  Serial.println("WiFi connected");<br>
  Serial.println(WiFi.localIP());<br>
  ThingSpeak.begin(client);<br>
  startMillis = millis();  //initial start time<br>
}<br>
void loop()<br>
{<br>
  digitalWrite(trigPin1, LOW);<br>
  delayMicroseconds(2);<br>
  digitalWrite(trigPin1, HIGH);<br>
  delayMicroseconds(10);<br>
  digitalWrite(trigPin1, LOW);<br>
  duration1 = pulseIn(echoPin1, HIGH);<br>
  distance1 = duration1 * 0.034 / 2;<br>
  Serial.println(distance1);<br>
  if (distance1 <= 400)<br>
  {<br>
    digitalWrite(D0, HIGH);<br>
    tone(BUZZER, 300);<br>
    digitalWrite(D1, LOW);<br>
    delay(1500);<br>
    noTone(BUZZER);<br>
  }<br>
  else<br>
  {<br>
    digitalWrite(D1, HIGH);<br>
    digitalWrite(D0, LOW);<br>
  }<br>
  currentMillis = millis();<br>
  if (currentMillis - startMillis >= period)<br>
  {<br>
    ThingSpeak.setField(1, distance1);<br>
    ThingSpeak.writeFields(ch_no, write_api);<br>
    startMillis = currentMillis;<br>
  }<br>
}<br>




ESP32 SOFTWARE PROGRAM:-

https://wokwi.com/projects/340852517819646547 ( led blink)
https://wokwi.com/projects/340852963452912210 (3 LED)
https://wokwi.com/projects/340853325803029074 (RGB MULTICOLOR)
https://wokwi.com/projects/340853653389705812 ( RGB COLOR)
https://wokwi.com/projects/340854854168609362 (LCD )
https://wokwi.com/projects/340857446725583442 (servomotor with sliding potentiometer)
https://wokwi.com/projects/340892440485429842 (DHT22)
