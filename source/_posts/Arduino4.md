---
title: Arduino感光燈
date: 2018-04-28 17:55:15
tags: Arduino
---

<hr>

```bash
int led = 13;  //設定LED燈的接腳
int val = 0;   //設定讀取光敏電阻的電壓值名稱
void setup() {
  pinMode(led,OUTPUT);  //設定LED燈為輸出
  Serial.begin(9600);   //設定串口波特率
}

void loop() {
  val = analogRead(0);      //讀取電壓值
  Serial.println(val);      //顯示在監控串口
  if(val>1000){                 //如果電壓值大於1000
    digitalWrite(led,HIGH);     //LED燈亮
  }
  else{
    digitalWrite(led,LOW);      //否則LED熄滅
  }
}
```
監控視窗

還沒遮住光敏電阻時所讀出的數值
<img src="https://i.screenshot.net/p/pmjezt1?2a9966d6c2339dba61493ed01747708c">

已經遮住光敏電阻所讀出的數值
<img src="https://i.screenshot.net/nze40uj">

我們可以看到有沒有遮住所讀到的電壓值有明顯的差異，所以上面的if函式中的電壓值可以隨著測到的值做改變

<img src="https://i.screenshot.net/n6vk0aw">

<hr>