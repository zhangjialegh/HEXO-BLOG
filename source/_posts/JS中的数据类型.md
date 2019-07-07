---
title: js中的数据类型
date: 2017-2-06
tags: [js]
categories: js基础
---

## 基本数据类型

 - null 代表一个空
 - undefined 代表未定义
 - number 代表数字类型
 - string 代表字符串
 - boolean 代表布尔值

## 复杂数据类型（引用数据类型）

 - 对象 (JS里面出了基本数据类型，其他的都是对象)
 - 数组 [ ]
 - 函数function fn(){ }
 - DOM元素
 - { }
 - ......
 


----------


## 区分数据类型

*使用一元操作符typeof*

### 基本使用 ：typeof 数据

 - *typeof所判断的数据类型的返回信息的数据类型是string*
 

----------


### JS中的数据类型之间的转换一共可以转为3种类型

>  - 数字
>  - 字符串
>  - 布尔值


----------
### Null类型只有一个数值：null

    typeof null==='object'

### undefined类型只有一个值：undefined

>  1. 一般情况下某个变量声明了但是没有赋值的时候
>  2. 某个对象的属性不存在的时候去访问这个属性的时候
>  3. *undefined类型实质上派生自null类型所有当undefined ==null ==>true


### 如何判断一个数据是不是Null

>if(xxx ===null){
    如果条件成立就证明是null
    }
    
    console.log(undefined == null);  //true
    console.log(undefined === null );//false

    

