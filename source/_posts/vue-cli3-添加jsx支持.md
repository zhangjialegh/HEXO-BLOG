title: vue-cli3 添加jsx支持
author: zjl
tags:
  - vue
categories: []
date: 2019-09-23 16:25:00
---
**在 `babel.config.js`文件**
```js
module.exports = {
  presets: [
   "@vue/cli-plugin-babel/preset",
   "@vue/babel-preset-jsx"
  ],
  "plugins": ["@babel/plugin-syntax-jsx"]
}

```
**同时需要安装**

```bash
npm install --save-dev @babel/plugin-syntax-jsx
npm install --save-dev @vue/babel-preset-jsx 
npm install --save-dev @vue/babel-helper-vue-jsx-merge-props
```