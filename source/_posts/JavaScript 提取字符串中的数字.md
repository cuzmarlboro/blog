---
title: JavaScript 提取字符串中的数字
date: 2019-12-24 23:29:53
tags: JavaScript
categories: 前端搬砖
---

1. 前面带数字,后面非数字,可以直接用parseFloat()函数
```js
let num = parseFloat("2.89元"); // num : 2.89
```

1. 字符串中只含有一个整型数值的字符串,直接使用正则表达式将数字的字符删除
```js
let str = '生于1999年';
let num = str1.replace(/[^\d]/g,' '); // num : 1999
```
1. 字符串中含有多数值,使用字符串的match方法,通过正则表达式提取字符串的所有数字(包含整数和小数)
```js
let str = '大米:2.57斤/元,白菜:3.65元/斤';
let arr = str.match(/\d+(.\d+)?/g);   // arr: ["2.75","3.65"]
```