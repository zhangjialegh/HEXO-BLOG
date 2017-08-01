---
title: js中Math对象
data: 2017-2-20
tags: [js,Math]
categories: js基础
---

## 常用对象
 1. Math.PI  *（圆周率）*
 2. Math.abs() *（求绝对值）*
 3. Math.random() *(随机数)*
 4. Math.round() *（四舍五入）*
 5. Math.sin(rad) *(三角函数的正弦值):返回[-1,1]之间的数*
 6. Math.cos(rad) *(三角函数的余弦值):返回[-1,1]之间的数*
 7. Math.tan(rad) *(三角函数的正切值):返回[-1,1]之间的数*
 8. Math.atan(x) *(三角函数的反正切值):返回[-pi/2,pi/2]之间的数*
 9. Math.atan2(dy,dx) *(返回值是[-pi,pi]之间的数)*
 10. Math.floor(n) *向下取整*
 11. Math.ceil(n) *向上取整*
 12. Math.pow(x,n) *求x的n次幂*
 13. Math.sqrt(x,n) *求x的n次方根*
 14. Math.max(n1,n2,n3...) *求最大值*
 15. Math.min（n1,n2,n3...) *求最小值*
 16. （x ** y）x的y次幂 （ES6的新运算符）
 
## 用法
1. 求最大或最小值
```
var arr=[3,4,5,7,6,2,29,94];
var max=Math.max(...arr),
    min=Math.min(...arr);
    
```
2. 取随机数
 
```
var n=Math.round(Math.random()*(max-min)+min);  //获取[min,max]之间的随机整数

```


