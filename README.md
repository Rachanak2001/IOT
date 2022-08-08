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

![image](https://user-images.githubusercontent.com/97940850/182358111-4c419a1d-794c-43d8-b235-596bd407dbc6.png)

**Chassing LED**
int pinsCount=7;                        // declaring the integer variable pinsCount
int pins[] = {D0,D1,D2,D3,D4,D5,D6};          // declaring the array pins[]
 
void setup() {                
  for (int i=0; i<pinsCount; i=i+1){    // counting the variable i from 0 to 9
    pinMode(pins[i], OUTPUT);            // initialising the pin at index i of the array of pins as OUTPUT
  }
}
 
void loop() {
  for (int i=0; i<pinsCount; i=i+1){    // chasing right
    digitalWrite(pins[i], HIGH);         // switching the LED at index i on
    delay(100);                          // stopping the program for 100 milliseconds
    digitalWrite(pins[i], LOW);          // switching the LED at index i off
  }
 for (int i=pinsCount-1; i>0; i=i-1){   // chasing left (except the outer leds)
   digitalWrite(pins[i], HIGH);         // switching the LED at index i on
   delay(100);                          // stopping the program for 100 milliseconds
  digitalWrite(pins[i], LOW);          // switching the LED at index i off
  
}
}
