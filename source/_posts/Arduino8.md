---
title: Arduino RGB燈
date: 2018-04-30 16:57:04
tags: Arduino
---

```bash
int red = 10;
int green = 9;
int blue = 6;
int rval = 0;
int gval = 0;
int bval = 0;
void setup() {
  pinMode(red,OUTPUT);
  pinMode(green,OUTPUT);
  pinMode(blue,OUTPUT);
}

void loop() {
  rval=random(0,255);  //在0到225中隨機存取一個數字
  gval=random(0,255);
  bval=random(0,255);
  analogWrite(red,rval);    //將存取的數字寫入led燈內
  analogWrite(green,gval);
  analogWrite(blue,bval);
  delay(500);              //延遲半秒
}
```

<font color="#FF0000">random(min,max)</font>這個函式是在一個範圍內存取隨機的數字，範圍就是括號中的最大值跟最小值

<blockquote class="imgur-embed-pub" lang="en" data-id="a/aKDadzl"><a href="//imgur.com/aKDadzl"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>