---
title: chorme浏览器记住密码后input黄色背景处理方法总结（三种）
date: 2018-02-28 17:11:56
tags: 
 - CSS
 - JavaScript
categories: 
- 前端开发
---

# 解决方法

## 方法1：阴影覆盖

input:-webkit-autofill {
-webkit-box-shadow: 0 0 0 1000px white inset !important;
}
注：由于是设置颜色覆盖，所以只对非透明的纯色背景有效；

## 方法2：修改chrome浏览器渲染黄色背景的时间（推荐）

:-webkit-autofill {
-webkit-text-fill-color: #fff !important;
transition: background-color 5000s ease-in-out 0s;
}
注：此方法适用于上图那种背景为透明色的输入框

## 方法3：jq方式去除

```bash
if (navigator.userAgent.toLowerCase().indexOf("chrome") >= 0)
{
  let _interval = window.setInterval(function () {
    let autofills = $('input:-webkit-autofill');
    if (autofills.length > 0) {
      window.clearInterval(_interval); // 停止轮询
      autofills.each(function() {
        let clone = $(this).clone(true, true);
        $(this).after(clone).remove();
      });
    }
  }, 20);
}
```

## 转载自

[chorme浏览器记住密码后input黄色背景处理方法总结（三种）](https://segmentfault.com/a/1190000013381998)