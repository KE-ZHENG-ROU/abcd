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
