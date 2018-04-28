---
title: Arduino手動旋轉伺服馬達
date: 2018-04-28 20:30:15
tags: Arduino
---

我這邊先測了可變電阻所提供的數值範圍
```bash
int val = 0;
void setup() {
 Serial.begin(9600);
}
void loop() {
  val=analogRead(0);
  Serial.println(val);
}
```

<blockquote class="imgur-embed-pub" lang="en" data-id="C6ySkg2"><a href="//imgur.com/C6ySkg2"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

結果得知10k的可變電阻提供的數值範圍為0~1023

```bash
#include <Servo.h>
Servo test;
int val = 0;
void setup() {
 test.attach(8);
}

void loop() {
  val=analogRead(0);
  val=map(val,0,1023,0,180);
  test.write(val);
  delay(15);
}
```

這裡主要講解map函式

格式如下：
map(value, fromLow, fromHigh, toLow, toHigh)

map 這個函數的作用是將一個範圍的數字映射到另一個範圍的數字

也就是說，會將 fromLow 到 fromHigh 之間的值映射在 toLow 在 toHigh 之間

map 函數參數：

value：需要映射的值

fromLow：範圍值的下限

fromHigh：範圍值的上限

toLow：目標範圍值的下限

toHigh：目標範圍值的上限

<blockquote class="imgur-embed-pub" lang="en" data-id="VgP6nbk"><a href="//imgur.com/VgP6nbk"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>