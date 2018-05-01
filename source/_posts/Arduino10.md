---
title: Arduino繼電器開關
date: 2018-05-01 21:20:55
tags:  Arduino
---

```bash
int bottonpin = 2;                          //按鈕腳位設定
int relaypin = 3;                           //繼電器腳位設定
int relaystate=digitalRead(relaypin);       //讀取第三腳的狀態儲存在relaystate裡面
void setup() {
  pinMode(bottonpin,INPUT);                 //按鈕為輸入
  pinMode(relaypin,OUTPUT);                 //繼電器為輸出
  Serial.begin(9600);
}

void callswich() {                          //副程式開頭
  if(relaystate == LOW){                    //如果繼電器狀態為LOW，就轉為HIGH
    relaystate=HIGH;
  }
  else{
    relaystate=LOW;                         //否則就轉為LOW
  }
  digitalWrite(relaypin,relaystate);        //將繼電器狀態寫入
}

void loop() {
  int bottonstate=digitalRead(bottonpin);   //讀取按鈕狀態儲存在bottonstate裡面
  if(bottonstate==HIGH){                    //如果按鈕狀態為HIGH
    callswich();                            //呼叫副程式
    delay(500);                             //讓按鈕的間距時間為半秒
    Serial.print("state=");
    Serial.println(relaystate);
  }
}
```
## 繼電器開關的狀態

<blockquote class="imgur-embed-pub" lang="en" data-id="a/seJWLZl"><a href="//imgur.com/seJWLZl"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

<blockquote class="imgur-embed-pub" lang="en" data-id="a/eiPEpGf"><a href="//imgur.com/eiPEpGf"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>