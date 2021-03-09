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
