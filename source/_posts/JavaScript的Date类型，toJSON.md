---
title: JavaScript的Date类型，toJSON
date: 2018-01-23 20:34:02
tags: 
 - Angular
 - TypeScript
 - JavaScript
categories: 
- 前端开发
---
# 你肯定也被坑过

最近在项目中遇到了一个问题，前端Date类型数据没经过任何处理，提交到服务端之后时间变了。

```bash
new Date()
// Tue Jan 23 2018 20:39:12 GMT+0800 (中国标准时间)
```

看上去没有任何问题的时间，但实际在提交到服务端时，发现浏览器里面传过去的参数已经变成了下面这样。

```bash
"2018-01-23T12:39:17.211Z"
```

原因是在ajax提交数据时其实并没有什么Date类型，只能是一个json字符串，这个时间字符串其实就是

```bash
new Date().toJSON()
// 2018-01-23T12:39:17.211Z
```

其实这是一个 ``ISO 8601`` 时间

## ISO 8601

国际标准化组织的国际标准ISO 8601是日期和时间的表示方法，全称为《数据存储和交换形式·信息交换·日期和时间的表示方法》。目前最新为第三版ISO8601:2004，第一版为ISO8601:1988，第二版为ISO8601:2000。年由4位数组成，以公历公元1年为0001年，以公元前1年为0000年，公元前2年为-0001年，其他以此类推。应用其他纪年法要换算成公历，但如果发送和接受信息的双方有共同一致同意的其他纪年法，可以自行应用。

```bash
YYYY-MM-DDThh:mm:ss ± timezone(时区用HH:MM表示)
1997-07-16T08:20:30Z
// “Z”表示UTC标准时区，即"00:00",所以这里表示零时区的`1997年7月16日08时20分30秒`
//转换成位于东八区的北京时间则为`1997年7月17日16时20分30秒`
1997-07-16T19:20:30+01:00
// 表示东一区的1997年7月16日19时20秒30分，转换成UTC标准时间的话是1997-07-16T18:20:30Z
```

## Angular + TypeScript

我们项目中用到了 ``TypeScript``，对象使用的是强类型，所以提交数据的时候是有一个 ``JSON.stringify()`` 的转换，在这个过程中 ``Date`` 类型就会调用 ``toJSON()`` 的方法转换成字符串。

## 解决

* 在提交之前把 ``Date`` 类型改为 ``String`` 类型，不用 ``toJSON()`` 方法，提前转换成正确的字符串。

* 修改 ``toJSON()`` 方法，比如这样

```bash
Date.prototype.toJSON = function(){return this.toUTCString();};
```

## Reference

[JavaScript 时间与日期处理实战:你肯定被坑过](https://segmentfault.com/a/1190000007581722)
[JS原生Date类型方法的一些冷知识](http://chitanda.me/2015/08/21/the-trivia-of-js-date-function/)
[阮一峰 JavaScript标准参考教程 Date对象](http://javascript.ruanyifeng.com/stdlib/date.html#toc4)