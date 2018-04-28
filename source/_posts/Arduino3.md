---
title: Arduino 震動感測器
date: 2018-04-27 22:00:21
tags: Arduino
---

```bash
int led = 13;
int sensor = 2; //震動感測器
unsigned char number = 0; //unsigned char = 255
void setup() {
  pinMode(led,OUTPUT);
  pinMode(sensor,INPUT);
  attachInterrupt(0,work,RISING); //中斷程式
}

void loop() {
 if(number!= 0){      //如果條件numder不等於0
  number = 0;         // number=0
  digitalWrite(led,HIGH); //led亮
  delay(1000); //1秒
 }
 else{
  digitalWrite(led,LOW);  //否則led滅
 }
}
void work(){
  number++;   //numder一直加
}
```

本篇最重要的觀念就是教大家何謂中斷程式，以及如何去使用它
中斷程式就是當狀況發生時，停止現在正在運行的程式，去執行中斷程式，等到狀況解除後再回來執行原本的程式
<font color="#FF0000">attachInterrupt()</font>就是中斷程式的語法
attachInterrupt(interrupt, function, mode)
interrupt:接腳，有0和1兩種，0對應的接腳為Pin2；1對應的接腳為Pin3
function:中斷程式的名稱
mode:狀態，說明感測器發生甚麼事時觸發中斷程式，只有以下四種情況
    LOW：當腳位為低電位時，觸發中斷
    CHANGE 當腳位電位發生改變時，觸發中斷
    RISING 當腳位從低電轉成高電位時，觸發中斷
    FALLING 當腳位從高電位轉為低電位時，觸發中斷
<img src="https://sites.google.com/a/jbps.ttct.edu.tw/zhi-ben-guo-xiaoarduino-yan-xi/_/rsrc/1459913936278/di-shi-san-ke-qing-xie-kai-guan-led-deng-pao/Ardulno%20SW-520D%20720.jpg?height=356&width=400">

<iframe class="imgur-embed" width="100%" height="540" frameborder="0" src="https://i.imgur.com/KoucSI5.gifv#embed"></iframe>