---
title: Arduinon伺服馬達
date: 2018-04-28 19:39:37
tags: Arduinon
---

```bash
#include <Servo.h>
Servo test;
int pos = 0;
void setup() {
 test.attach(8);
}

void loop() {
  for(pos=0;pos<=180;pos+=1){
    test.write(pos);
    delay(15);
  }
  for(pos=180;pos>=0;pos-=1){
    test.write(pos);
    delay(15);
  }
}
```
伺服馬達:伺服馬達和步進馬達最大的差異就是在伺服馬達驅動後會回傳脈波訊號，告訴控制端多轉了多少，並且自動補正

        各有優缺點伺服馬達因為會不斷補正的因素，導致整個馬達會震動，那步進馬達就不會有這樣的問題，而且相較

        之下步進馬達也比較便宜

<font size="5">步進馬達</font>
<img src="http://3.bp.blogspot.com/-knaHf-j01lY/VqTPy_NpH-I/AAAAAAAAAkI/yrObv7fwXiM/s1600/2016-01-24_202447.jpg">

<font size="5">伺服馬達</font>
<img src="http://fami3d.com/wp-content/uploads/2016/09/%E4%BC%BA%E6%9C%8D%E9%A6%AC%E9%81%94%EF%BC%8D%E7%9B%B8%E8%8B%A5%E6%96%BCTower-Pro-SG90.jpg">

伺服馬達總共有三條線，紅色的是接火線，棕色(黑色)的是接地線，橙色的是接訊號源


<font color="#FF0000" size="5">Servo.h</font>是一個Arduino內建的函式庫裏面包含伺服馬達相關的函式，我們第一行把它調出來使用

<font color="#FF0000" >Servo test; </font>創建一個馬達名稱

<font color="#FF0000" >test.attach(8); </font>這裡開始使用Servo中的函式了，和以前函式使用有點不同。這裡，我們要

先指出對象的名稱，在指出函式的名稱

<img src="https://i.screenshot.net/l2lvycq">