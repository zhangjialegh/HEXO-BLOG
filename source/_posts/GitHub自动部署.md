title: GitHub自动部署
author: zjl
tags:
  - nodejs
categories:
  - nodejs
date: 2019-02-21 00:19:00
---
# GitHub自动部署代码

[Demo地址](https://github.com/zhangjialegh/WebHooks)

## 第一步：添加webhooks

![image](https://gitlab.com/zhangjiale/ifile/raw/master/webhooks1.jpg)

![image](https://gitlab.com/zhangjiale/ifile/raw/master/webhooks2.jpg)

## 第二部：可以选择nginx反向代理

```bash
server {
    ...
    
    location /webhooks/ {
       proxy_pass http://localhost:8003/webhooks/;
    }
    
    ...
}

```

## 第三部：配置后端接口和自动部署脚本

```javascript

/** 配置路由
* @router.js
* @handler : (Function) 执行函数
*/

app.post('/webhooks/xx', handler)

...




/** 执行函数
* @handler : (Function) 执行函数
*/

function handler () {
    // 这里我选择用 child_process 执行脚本文件
}

...



/** 脚本文件
* @deploy.sh
*/

#! /bin/bash

...


```