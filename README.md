# 2021/03/02
第一個程式 0-9 循環顯示
```c++
int a[10][7] ={ {1,1,1,1,1,1,0},
                {0,1,1,0,0,0,0},
                {1,1,0,1,1,0,1},
                {1,1,1,1,0,0,1},
                {0,1,1,0,0,1,1},
                {1,0,1,1,0,1,1},
                {1,0,1,1,1,1,1},
                {1,1,1,0,0,0,0},
                {1,1,1,1,1,1,1},
                {1,1,1,1,0,1,1}};
void setup() {
int i;
for (i = 2; i<13;i++)
  pinMode(i,OUTPUT);
}
void loop() {
  digitalWrite(9,HIGH);
for (int j = 0;j<10;j++)
  {for (int i = 2; i<9;i++)
  digitalWrite(i,a[j][i-2]);
  delay(200);}
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/177D5621-F04B-464F-B83F-F600F15D653A.jpeg)
--------------------------------------------------------------------------------------------------

# 2021/03/02-2
第二個程式 顯示不同數字 
```c++
int a[10][7] ={
{1,1,1,1,1,1,0},
{0,1,1,0,0,0,0},
{1,1,0,1,1,0,1},
{1,1,1,1,0,0,1},
{0,1,1,0,0,1,1},
{1,0,1,1,0,1,1},
{1,0,1,1,1,1,1},
{1,1,1,0,0,0,0},
{1,1,1,1,1,1,1},
{1,1,1,1,0,1,1}
};
float c;
int b[4][4] ={
  {1,0,0,0},
  {0,1,0,0},
  {0,0,1,0},
  {0,0,0,1},
};
int d[4] = {9,2,4,7};
void setup() {
int i;
for (i = 2; i<13;i++)
  pinMode(i,OUTPUT);
  c = millis();
  Serial.begin(9600);
}
void loop() {
for (int j = 0;j<4;j++){
for(int k=9;k<13;k++)
   digitalWrite(k,b[j][k-9]);
   for(int i=2;i<9;i++)
     digitalWrite(i,a[d[j]][i-2]);
   delay(5);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/8D945D99-1530-4FDD-81B1-9291D229645C.jpeg)
---------------------------------------------------------------------------------------------------
# 2021/03/09
第三個程式 按鈕控制LCD文字位置
```c++
#include <LiquidCrystal.h>
LiquidCrystal lcd(12,11,5,4,3,2);
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B10001,
  B01110,
  B00000,
};
bool haha=1,haha2=1;
void setup() {
  Serial.begin(9600);
  pinMode(8,1);
  pinMode(9,1);
  lcd.begin(16,2);
  lcd.noCursor();
  lcd.createChar(0,smiley);
  lcd.clear();
  lcd.print("The light");
}
void loop() {
  if(digitalRead(8))
  {
    while(digitalRead(8));{delay(20);}
    lcd.scrollDisplayLeft(); 
  }
  
  if(digitalRead(9))
  {
    while(digitalRead(9));{delay(20);}
    lcd.scrollDisplayRight(); 
  }
  Serial.print(digitalRead(8));
  Serial.print(digitalRead(9));
  Serial.println(haha);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/9A5A823A-2A63-4BBB-956D-4363B164B6F6.gif)
-----------------------------------------------------
# 2021/03/09 -1
第四個 LCD右移
```c++
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {
  lcd.begin(16, 2);
  lcd.print("hey");
}
void loop() {
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,1);
  lcd.print("aaaaaaaaaa");
  lcd.scrollDisplayRight();
  lcd.noBlink();
  delay(3000);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/1ADDFF83-0BE1-4EB8-AFC6-ABCB45D59A0B.gif)
------------------------------------------------------
# 2021/03/09 -2
第五個 LCD顯示圖形 
```c++
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B10001,
  B01110,
  B00000,
};
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {
  lcd.begin(16, 2);
  lcd.print("moon");
}
void loop() {
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,1);
  lcd.createChar(0, smiley);
  lcd.setCursor(0,1);
  lcd.write(byte(0));
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/2B4DD6A1-5E42-4F72-8233-1FCB5BB267B8.gif)
------------------------------------------------------------
# 2021/03/09-3
第六個 LCD圖形循環顯示
```c++
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B10001,
  B01110,
  B00000,
};
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {
  lcd.begin(16, 2);
  lcd.print("hey!");
}
void loop() {
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,1);
  lcd.createChar(0, smiley);
  for(int i=0;i<16;i++){
  delay(100);
  lcd.setCursor(i,1);
  lcd.write(byte(0));
  }
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/8EFF27E0-7B53-408E-B0F1-593E24BCA979.gif)
------------------------------------------------------------
# 2021/03/16
第七個 風扇三段轉速控制
```c++
void setup() {
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
}
void loop() {
  for(int i=80;i<255;i+=86){
    analogWrite(5,i);
    analogWrite(6,0);
    delay(5000);
  }
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/82D9BA87-072D-4021-A5C7-DCFECF24475D.gif)
------------------------------------------------------------
# 2021/03/16 -1
第八個 按鈕控制風扇轉速大小
```c++
int i;
void setup() {
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
  pinMode(2,INPUT);
  Serial.begin(9600);
}
void motor(int i) {
  analogWrite(5,i);
  analogWrite(6,0);
}
void loop() {
  Serial.println(i);
  if(digitalRead(2)==LOW) {
    while(digitalRead(2)==LOW);
    i=i+35;
  }
  else if(digitalRead(3)==LOW)  {
    while(digitalRead(3)==LOW);
    i=i-35;
    }
  else if(digitalRead(4)==LOW){
    while(digitalRead(4)==LOW);
    i=90;
    }
  else if(digitalRead(7)==LOW){
    while(digitalRead(7)==LOW);
    i=0;    
  }
  if(i>=255) {
    i=255;
  }
  else if(i<=0) {
    i = 0;
  }
  motor(i);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/D5F930C2-E416-4C0E-84FA-654DE2FC4638.gif)
------------------------------------------------------------
# 2021/03/30
第九個 溫濕度感應器，溫度達設定數值即使蜂鳴器作動
```c++
// DHT Temperature & Humidity Sensor
// Unified Sensor Library Example
// Written by Tony DiCola for Adafruit Industries
// Released under an MIT license.

// REQUIRES the following Arduino libraries:
// - DHT Sensor Library: https://github.com/adafruit/DHT-sensor-library
// - Adafruit Unified Sensor Lib: https://github.com/adafruit/Adafruit_Sensor

#include <Adafruit_Sensor.h>
#include <DHT.h>
#include <DHT_U.h>

#define DHTPIN 2     // Digital pin connected to the DHT sensor 
// Feather HUZZAH ESP8266 note: use pins 3, 4, 5, 12, 13 or 14 --
// Pin 15 can work but DHT must be disconnected during program upload.

// Uncomment the type of sensor in use:
//#define DHTTYPE    DHT11     // DHT 11
#define DHTTYPE    DHT22     // DHT 22 (AM2302)
//#define DHTTYPE    DHT21     // DHT 21 (AM2301)

// See guide for details on sensor wiring and usage:
//   https://learn.adafruit.com/dht/overview

DHT_Unified dht(DHTPIN, DHTTYPE);

uint32_t delayMS;
double a;
void setup() {
  pinMode(3,OUTPUT);
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
  Serial.begin(9600);
  // Initialize device.
  dht.begin();
  sensor_t sensor;
  /*Serial.println(F("DHTxx Unified Sensor Example"));
  // Print temperature sensor details.
  
  dht.temperature().getSensor(&sensor);
  Serial.println(F("------------------------------------"));
  Serial.println(F("Temperature Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("°C"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("°C"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("°C"));
  Serial.println(F("------------------------------------"));
  // Print humidity sensor details.
  dht.humidity().getSensor(&sensor);
  Serial.println(F("Humidity Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("%"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("%"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("%"));
  Serial.println(F("------------------------------------"));
  // Set delay between sensor readings based on sensor details.*/
  delayMS = sensor.min_delay / 1000;
}
void Motor(int a){
  if(a == 1){
      digitalWrite(5,HIGH);
      digitalWrite(6,LOW);
    }
    else{
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
    }
}
void loop() {
  // Delay between measurements.
  delay(delayMS);
  // Get temperature event and print its value.
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  if (isnan(event.temperature)) {
    Serial.println(F("Error reading temperature!"));
  }
  else {
    Serial.print(F("Temperature: "));
    Serial.print(event.temperature);
    Serial.println(F("°C"));
    a = event.temperature;
  }
  // Get humidity event and print its value.
  dht.humidity().getEvent(&event);
  if (isnan(event.relative_humidity)) {
    Serial.println(F("Error reading humidity!"));
  }
  else {
    Serial.print(F("Humidity: "));
    Serial.print(event.relative_humidity);
    Serial.println(F("%"));
  }
  if(a>=27){
    tone(3,500);
    delay(500);
    noTone(3);
    delay(500);
    Motor(1);
  }
  Motor(0);
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/F071E9F3-7961-40E2-BBAC-4D8793C0CDEF.jpeg)
----------------------------------
# 2021/03/30 -1
第十個 溫濕度感應器，溫度達設定數值即啟動風扇
```c++
// DHT Temperature & Humidity Sensor
// Unified Sensor Library Example
// Written by Tony DiCola for Adafruit Industries
// Released under an MIT license.

// REQUIRES the following Arduino libraries:
// - DHT Sensor Library: https://github.com/adafruit/DHT-sensor-library
// - Adafruit Unified Sensor Lib: https://github.com/adafruit/Adafruit_Sensor

#include <Adafruit_Sensor.h>
#include <DHT.h>
#include <DHT_U.h>

#define DHTPIN 2     // Digital pin connected to the DHT sensor 
// Feather HUZZAH ESP8266 note: use pins 3, 4, 5, 12, 13 or 14 --
// Pin 15 can work but DHT must be disconnected during program upload.

// Uncomment the type of sensor in use:
//#define DHTTYPE    DHT11     // DHT 11
#define DHTTYPE    DHT22     // DHT 22 (AM2302)
//#define DHTTYPE    DHT21     // DHT 21 (AM2301)

// See guide for details on sensor wiring and usage:
//   https://learn.adafruit.com/dht/overview

DHT_Unified dht(DHTPIN, DHTTYPE);

uint32_t delayMS;
double a;
void setup() {
  pinMode(3,OUTPUT);
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
  Serial.begin(9600);
  dht.begin();
  sensor_t sensor;
  /*Serial.println(F("DHTxx Unified Sensor Example"));
  // Print temperature sensor details.
  dht.temperature().getSensor(&sensor);
  Serial.println(F("------------------------------------"));
  Serial.println(F("Temperature Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("°C"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("°C"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("°C"));
  Serial.println(F("------------------------------------"));
  // Print humidity sensor details.
  dht.humidity().getSensor(&sensor);
  Serial.println(F("Humidity Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("%"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("%"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("%"));
  Serial.println(F("------------------------------------"));
  // Set delay between sensor readings based on sensor details.*/
  delayMS = sensor.min_delay / 1000;
}
void Motor(int a){
  if (a == 1) {
      digitalWrite(5,HIGH);
      digitalWrite(6,LOW);
    }
    else {
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
    }
}
void loop() {
  // Delay between measurements.
  delay(delayMS);
  // Get temperature event and print its value.
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  if (isnan(event.temperature)) {
    Serial.println(F("Error reading temperature!"));
  }
  else {
    Serial.print(F("Temperature: "));
    Serial.print(event.temperature);
    Serial.println(F("°C"));
    a = event.temperature;
  }
  // Get humidity event and print its value.
  dht.humidity().getEvent(&event);
  if (isnan(event.relative_humidity)) {
    Serial.println(F("Error reading humidity!"));
  }
  else {
    Serial.print(F("Humidity: "));
    Serial.print(event.relative_humidity);
    Serial.println(F("%"));
  }
  if (a >= 27) {
    tone(3,500);
    delay(500);
    noTone(3);
    delay(500);
    Motor(1);
  }
  else{
    Motor(0);
  }
}
```
電路圖如下：
![image](https://github.com/KE-ZHENG-ROU/abcd/blob/main/87830ADC-813E-43AC-8F6F-D6634D79B2C4.jpeg)
---------------------------------------
