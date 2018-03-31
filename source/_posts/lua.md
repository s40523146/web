---
title: lua practice
tags: lua
editor: 謝秉軒
date: 2018-03-31 00:00:00
---

## 字串
``` bash
>print('aabbcc')
aabbcc
>print("aabbcc")
aabbcc
>print([[aabbcc]])
aabbcc
>print([=aabbcc=])
aabbcc
```
## 賦值
``` bash
>a,b,c,d = ture，false，1，1<2
print(a，b，c，d)=ture，false，1，ture
```
## 比較
``` bash
>print(1==1)
ture
>print(1~=1)
false
```
## nil空
``` bash
>a，b，c，d=1，2
a，b，c，d=1，2，nil，nil
```
## 邏輯判斷
``` bash
print(1 and 1)
1
print(1 or nil)
1
print(not nil)
ture
```
## 字串連結
``` bash
>print("hello".."world")
helloworld
```
## 計算長度
``` bash
print(#"hello")
5
```
## 註解
``` bash
--說明程式
快捷鍵:contrl+/
```
## if條件式
``` bash
if 1==1 then
    print("yes")
end
yes
```
## while條件式
``` bash
while 1==2 do
    print("never print")
end
```
## for迴圈
``` bash
for i = 1,3 do
print(i)
end
1 2 3

for i = 1,10,2 do
print(i)
end
1 3 5 7 9
```
## repeat迴圈(至少執行一次)
``` bash
repeat print ("yes") until 1<10 
yes
```
## break
``` bash
for i = 1,10 do
    if i>5 then
        break
        end
print(i)
end

1,2,3,4,5
```
## 呼叫函式
``` bash
function test()
    print("a")
    end
test()

a
```