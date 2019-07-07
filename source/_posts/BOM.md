---
title: BOM(浏览器对象模型)
date: 2017-5-11
tags: [js]
categories: js基础
---

*Browser Object Model 浏览器对象模型，它的核心是 window ，同时这个window还是js的顶级对象。*

## window.navigator.userAgent

  可以获取到当前浏览器的内核信息以及用户代理信息

```
function isMb(){
      var ret = false;
      var ui = ['iPhone', 'iPad', 'Android'];
      var userAgent = window.navigator.userAgent;
      ui.forEach(function(item, i) {
        if(userAgent.indexOf(item) !== -1){
          ret = true;
        }
      });
      return ret;
    }
```

## window.location.href

  可以获取或者设置url的信息

## window.location.hash

  包括#后后面的东西，当设定hash的时候浏览器窗口不会刷新

## window.location.search

  获取到 '?' 到 '#'之间的包括 '?' 的部分，如果修改了search 会刷新浏览器页面
```
https://www.baidu.com/s?wd=react&rsv_spt=1#a=1&b=2
    
https://www.baidu.com/abc/game.html?wd=react&rsv_spt=1#a=1&b=2  ===> href

https:// ===> protocol

/abc/game.html  ===> path

/  ===> root 根目录

?wd=react&rsv_spt=1  ===> search

#a=1&b=2  ===> hash

wd=react&rsv_spt=1  ===> querystring
```
## prompt

```
var res = prompt('请输入你的年龄');   

console.log(res);// 输入的内容如果没有输入就是null
```
## confirm

```
var res = confirm('我帅么？');

console.log(res); // true / false
```

## onhashchange

*当hash改变的时候会触发 hashchange 事件*

```
window.onhashchange = function (){
      alert(window.location.hash)
    };
```

