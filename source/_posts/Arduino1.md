---
title: Arduino 紅綠燈呼吸燈練習
date: 2018-04-11 17:06:56
tags: Arduino
---
# 呼吸燈
``` bash
int brightness = 0; 
int increase = 5;

void setup () {
  pinMode(3,OUTPUT);
}

void loop () {
  analogWrite(3,brightness);
  brightness = brightness + increase;
  if (brightness<=0 || brightness>=225){
    increase = -increase;
  }
delay(30);
}
```
&gt; analogWrite(pin,value)
analogWrite()函數用于给 PWM 口写入一个 0~255 的模擬值。特别注意的是，
analogWrite()函數只能寫入具有 PWM 功能的數字引脚。
Arduino引腳具有PWM功能的引腳會有"~"的標誌
脈波寬度調變，簡稱脈寬調變，是將類比訊號轉換為脈波的一種技術，一般轉換後脈波的週期固定，但脈波的占空比會依類比訊號的大小而改變。
下圖為duty cycle為50%,75%與25%的波形，可以發現duty cycle越大，Pulse佔它的周期時間越長。背光亮度就是透過duty cycle調整，duty cycle越大，高度就越高
![IMAGE OF PWM](http://4.bp.blogspot.com/-jZoIOL9974A/U3TaUXi1Z5I/AAAAAAAAAV0/2_m6rX3LHBw/s1600/duty_cycle.JPG)

# 互動紅綠燈

``` bash
  int carred = 12;
  int caryellow = 11;
  int cargreen = 10;
  int button = 9;
  int red = 8;
  int green = 7;
  unsigned long changeTime; 
void setup() {
  pinMode(carred,OUTPUT);
  pinMode(caryellow,OUTPUT);
  pinMode(cargreen,OUTPUT);
  pinMode(button,INPUT);
  pinMode(red,OUTPUT);
  pinMode(green,OUTPUT);
  digitalWrite(cargreen,HIGH); //設定初始燈泡
  digitalWrite(red,HIGH); //設定初始燈泡
}

void loop() {  --主程式
  int status = digitalRead(button); //status是讀取按鈕狀態
        if(state == HIGH && (millis() - changeTime)> 5000){
               changelight();  //如果botton是HIGH和changTime小於5000呼叫副程式changlight
        }
  }
  
void changelight() {
  digitalWrite(cargreen,LOW);
  delay(1000);
  digitalWrite(caryellow,HIGH);
  delay(1000);
  digitalWrite(caryellow,LOW);
  delay(1000);
  digitalWrite(carred,HIGH);
  delay(500);
  digitalWrite(red,LOW);
  delay(2000);
  digitalWrite(green,HIGH);
  delay(5000); //允許行人通過的時間
  for (int x=0 ; x<10 ; x++){ //行人綠燈閃爍警告
    digitalWrite(green,HIGH);
    delay(250);
    digitalWrite(green,LOW);
    delay(250);
    }
  digitalWrite(red,HIGH);
  delay(1000);
  digitalWrite(carred,LOW);
  delay(1000);
  digitalWrite(caryellow,HIGH);
  delay(1000);
  digitalWrite(caryellow,LOW);
  delay(1000);
  digitalWrite(cargreen,HIGH);
  changeTime = millis(); //回傳changeTime時間值
}
```

&gt; unsigned long changeTime;

這是一個新的變量類型。我們之前，只用過"int"，它可以存放一個 -32768
到 32767 之間的整數。這次要創建的是一個 long 的變量类型，它可以存放一個
-2147483648 到 2147483647 之間的整數。而 unsigned long 則是不儲存負數，
所以儲存的範圍就從 0 到 4294967295.

下圖是各種變量儲存種類和範圍
![Image of data](http://c.biancheng.net/cpp/uploads/allimg/140316/1-1403161Z633114.png)


&gt; digitalRead(button);

讀取按鈕狀態

<pre><code>
if(status == HIGH && (millis() - changeTime)> 5000) {
 //呼叫changelight副程式
 changelight();
}
<code><pre>

&gt; millis()
是一個Arduino內建函数，它返回值是時間，
Arduino 開始計算執行程式到執行完畢的時間，也稱之為機器時間，就像一個隱形時鐘，從控制
器開始的那一刻起到結束回傳值，以毫秒為單位。

&gt; 運算邏輯符號
![image of abc](http://www.pcstar.com.tw/blog/wp-content/uploads/2013/08/3-45.jpg)

