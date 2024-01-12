---
title: 解决 replace( ) 只能替换一次
date: 2019-12-26 23:29:53
tags: JavaScript
categories: 前端搬砖
---
## 1 replace()介绍

● replace() 方法会对匹配到的第一个字串替换，如果需要替换所有，则需要使用正则\
● replace() 不会修改原字符串，而是会返回一个新的字符串

## 2 替换所有解决方案（利用正则）

```js
let str = "We are happy."
//替换一个
let str2 = str.replace(' ','?')  //We?are happy.
//替换所有
let str3 = str.replace(new RegExp(' ','g'),'?') //We?are?happy.
```

## 3 replaceAll 方法（ES2021）

replaceAll() ，可以对调用它的字符串进行全局替换； 接收两个参数： 第一个参数是字符串/正则（若传入正则，须是全局的）， 第二个参数是需要替换的新字符串； 返回一个新字符串；

```js
const str = '2-4-6-8-10'
const newStr = str.replaceAll('-', '+')
console.log(newStr) // 2+4+6+8+10
```
