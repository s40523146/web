---
title: Arguino入門
date: 2018-04-08 22:18:18
tags: Arduino
---
# 賦值
``` bash
int ledPin = 10;
```
int 變量類型
ledpin變量名稱

C語言中有一些特定的字串是不能用成是變量名稱的，比如 main，if，while 等。這些東西東常會用橙色來提醒。

分號不可少。

# 函數
函數就是內建個一個個功能套件，通過這些功能的整合，就组成了我們的整段代
碼，一個完整的功能實現。這些功能也可以被反覆利用。而 setup()和 loop()比较特殊，不能被反覆使用。

``` bash
void setup() {}
```
這裡包括兩個函數一個是setup()一個是void{}

先從setup()介紹，setup是用來用來初始化變量、
設置針腳的输出/输入、配置串口等等。每次 Arduino 重新啟動後，setup 函数只
運行一次。

void{}就是函數無返回值的信号，並且後面的括號内為空。

``` bash
pinMode(pin,mode)
```
pinmode是一個可以設置針腳模式的一個功能。
pin是腳號。
mode可以是input也可以是output。

``` bash
void loop() {
 digitalWrite(ledPin,HIGH);
 delay(1000);
 digitalWrite(ledPin,LOW);
 delay(1000);
}
```
Arduino在執行完setup()函釋的初始化和變量的定義後就會進入loop()中，顧名思義loop函數就是不斷的循環
，直到電源關閉或是按下復歸。
digitalWrite(pin,value)
這個函数的意思是：引脚 pin 在 pinMode() 的中被設置为 OUTPUT 模式時，其電壓將
會和設定值一樣，HIGH 为 5V（3.3V 控制板上為 3.3V），LOW 为 0V。我們這裡就是
给引腳 10（ledPin）一个 5V 的電壓，點亮了引腳 10 這個 LED。

``` bash
delay(1000);
```
延遲 1000 毫秒，相當於一秒。

``` bash
void setup() {
  pinMode(13, OUTPUT);
}
void loop() {
  digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);              // wait for a second
  digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);              // wait for a second
}
```