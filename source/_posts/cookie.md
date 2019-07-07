---
title: Cookie
date: 2017-4-20
tags: [js,web前端]
categories: js基础
---

## cookie 的构成

 - 名称（name）
 *名称是唯一的，不区分大小写，并且中文等字符必须经过 encodeURIComponent 编码过的。*
 - 值（value）
 *就是 名称对应的 value， 同样如果是中文等 必须经过 encodeURIComponent 编码。*
 - 域（domain）
 *指定 cookie对哪个域来说是有效的，如果没有明确，那么会被默认设置当前域。*
 - 路径（path）
 *表示访问哪个路径，才会向服务器发送cookie，默认是 '/'，也就是所有路径都可以访问，例如，设置了 www.baidu.com/abc/那么只有www.baidu.com/abc/ 或者 www.baidu.com/abc/xxx/xxx ...能访问这个 cookie，而 www.baidu.com/ 是访问不到的。*
 - 失效时间（expires）
 *表示 cookie何时被删除的时间戳，默认是关闭浏览器失效。*
 - 安全标志（secure）
 *secure 表示是否需要 https 链接。*

## 前端应用

    document.cookie = `name=value; expires=${new Date()}; domain=.aaa.com; path=/; secure`
    
## js封装
```
const cookie = {
    set(name, value, expires, domain, path, secure) {
        let cookie = encodeURIComponent(name) + '=' + encodeURIComponet(value);
        if (expires instanceof Date) {
            cookie += `; expires=` + expires;
        }
        if (domain) {
            cookie += `; domain=` + domain;
        }
        if (path) {
            cookie += `; path=` + path;
        }
        if (secure) {
            cookie += `; secure`;
        }
        document.cookie = cookie;
    },
    get(name) {
        const cookie = document.cookie;
        const searchName = encodeURIComponent(name);
        const reg = new RegExp('\\b' + searchName + '=([^;]*)\\b', 'i');
        const ret = cookie.match(reg);
        return ret ? ret[1] : '';
    },
    delete(name, expires, domain, path, secure) {
        this.set(name, '', new Date(0), domain, path, secure);
    }
}
```

