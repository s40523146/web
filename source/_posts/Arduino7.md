---
title: Arduino彩色調光台
date: 2018-04-30 16:31:02
tags:  Arduino
---

```bash
int red = 10;   //給紅燈10號接腳
int green = 9;  //給紅燈9號接腳
int blue = 6;   //給紅燈6號接腳
int rval = 0;   
int gval = 0;
int bval = 0;
void setup() {
  pinMode(red,OUTPUT);      //led燈為輸出
  pinMode(green,OUTPUT);    //led燈為輸出
  pinMode(blue,OUTPUT);     //led燈為輸出
  Serial.begin(9600);       //串口波特律9600
}

void loop() {
  rval=analogRead(0);       //讀取A0模擬數據
  gval=analogRead(1);       //讀取A1模擬數據
  bval=analogRead(2);       //讀取A2模擬數據
  rval=map(rval,0,1023,0,255);      //將模擬數據轉換為led燈的亮度
  gval=map(gval,0,1023,0,255);      //將模擬數據轉換為led燈的亮度
  bval=map(bval,0,1023,0,255);      //將模擬數據轉換為led燈的亮度
  analogWrite(red,rval);        //將亮度寫入LED裡面
  analogWrite(green,gval);      //將亮度寫入LED裡面
  analogWrite(blue,bval);       //將亮度寫入LED裡面
  Serial.println(rval);         //串口監視 測試用
```
<blockquote class="imgur-embed-pub" lang="en" data-id="a/USSSSp7"><a href="//imgur.com/USSSSp7"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>
