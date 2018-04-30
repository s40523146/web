---
title: Arduino溫度感測氣&蜂鳴器
date: 2018-04-30 22:41:08
tags: Arduino
---

# 蜂鳴器
```bash
float sinval;       //小數點型的命令字元
int tonval;
void setup() {
  pinMode(8,OUTPUT);
}

void loop() {
  for(int x=0;x<=180;x++){          //從0到180度執行完畢每次加一
    sinval=sin(x*0.01744444);       //sin值需要徑度，所以要將角度換算
    tonval=(sinval*1000)+2000;      //調整聲音頻率
    tone(8,tonval);
    delay(10);
  }
}
```

<font color="#FF0000">float</font>是小數點型的宣告，因為sin值通常為有小數點的數字，所以命令字元使用float。

<font color="#FF0000">tonval=(sinval*1000)+2000;</font>這裡我們先乘上1000，目的是不要讓蜂鳴器接收的頻率有小數點，我也不知道為甚麼沒有小數

點聲音會怪怪的，所以我們就按照教材給它乘1000，去除小數點，然後後面加2000目的是調整身聲音的頻率，加的數字越大，音調就越高；反之，聲音越低，就要

調小數字。

<font color="#FF0000">tone(pin,tonval);</font>

下面我們來介紹 tone 先關的三個函式

（1）tone(pin,frequency)

Pin 就是連接到蜂鳴器的引腳，frequency 是以 Hz 為單位的頻率值。

（2）tone(pin,frequency,duration)

這裡有個 duration，它是以毫秒為單位，表示聲音長度的常數。如果沒有指定 duration，聲音就會一直持續到下一個頻率的聲音出現。

（3）noTone(pin)

noTone(pin)函式，結束所有聲音。

# 溫度感測器

## 先測試溫度感測器是否正常和電壓溫度換算值
```bash
int val = 0;
int t = 0;
void setup() {
  Serial.begin(9600);
}

void loop() {
  val=analogRead(0);
  t=val* (5/10.24);
  Serial.println(t);
}
```
讀出值為60

<blockquote class="imgur-embed-pub" lang="en" data-id="a/rZFFFjz"><a href="//imgur.com/rZFFFjz"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

室溫為29度

<blockquote class="imgur-embed-pub" lang="en" data-id="a/g9sjXHN"><a href="//imgur.com/g9sjXHN"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

換算公式如下
<font color="#FF0000">data = (double) val * (5/10.24);</font>

感測器傳出的是電壓值，它的範圍在 0~1023，總共5v，分給1024份等於一份有0.00488，因為每度 10mV，所以60*0.00488/0.01=29.28

## 然後在打上if()函式和加入剛剛的蜂鳴器程式及完成

```bash
float sinval;
int tonval;
int val = 0;
int t = 0;
void setup() {
  pinMode(8,OUTPUT);
  Serial.begin(9600);               //監控溫度狀況
}

void loop() {
  val=analogRead(0);
  t=val* (5/10.24);
  if(t>32){                         //如果溫度大於32度
    for(int x=0;x<=180;x++){        //蜂鳴器就開始叫
      sinval=sin(x*0.01744444);
    tonval=(sinval*1000)+2000;
    tone(8,tonval);
    delay(10);
    }
  }   
  Serial.println(t);
}
```