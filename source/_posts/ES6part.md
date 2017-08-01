---
title: ECMAScript 6
data: 2017-6-11
tags: [js]
categories: js基础
---
## Set

 - 集合的基本概念：集合是由一组无序且唯一（即不能重复）的项组成的。这个数据结构使用了与有限集合相同的数学概念，应用在计算机的数据结构中。
 - 特点：key 和 value相同，没有重复的value
 - ES6提供了数据结构Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

---

### 1. 创建一个Set

    const s = new Set([1,2,3,3,{a:1}]);
    console.log(s);

### 2. Set类的属性
 
    console.log(s.size) //4

### 3. Set类的方法

    const s = new Set([1,2,3]);
##### 1.添加一个数据

**添加一个数据，返回Set结构本身**

    s.add('a').add('b').add('c');
    
##### 2.删除一个数据
**删除一个数据，返回一个布尔值，表示删除是否成功**

    console.log(s.delete('a'));
    //true
    console.log(s);
    //Set(5) {1, 2, 3, "b", "c"}
    console.log(s.delete('a'));
    //false
##### 3.是否有一个数据
**判断该值是否是Set的成员，返回一个布尔值**

    console.log(s.has('a'));
    //false
    console.log(s.has(1));
    //true
##### 4.清楚所有数据，没有返回值

    s.clear();
    console.log(s);
    //Set(0) {}
    
### 4.数组去重
```
const arr = [1,2,2,1,[],[],true,NaN,NaN,false,true,{a:1}];

console.log([...new Set(arr)]);
//[1, 2, Array(0), Array(0), true, NaN, false, Object]
```
### 5.返回键名的遍历器keys()

```
const k = new Set([1,2,3]);
console.log(k.keys());
//SetIterator {1, 2, 3}
```
### 6.返回键值的遍历器values()
```
console.log(k.values());
//SetIterator {1, 2, 3}
```
### 7.返回键值对的遍历器entries()
```
console.log(k.entries());
//SetIterator {1, 2, 3}
```

### 8.使用回掉函数遍历每个成员

```
k.forEach(function (value,key,set){
  console.log(key + 'ES6');
  //1ES6  2ES6  3ES6
 }
)
```
### 9.注意事项

 1. key 和 vaule是相同的
 2. NaN 和 NaN 认为是相同的
 3. { } 和 { } 是不同的

---
## Map

 - 字典：是用来存储不重复的key的Hash结构。不同于集合（Set）的是，字典使用的是[键，值]的形式来存储数据的。
 - JavaScript的对象（Object：{ }）只能用字符串当作键，这给它的使用带来了很大的限制。
 - 为了解决这个问题，ES6提供了Map数据结构。它类似于对象，也是键值对的集合，但是"键"的范围不限于字符串，各种类型的值（包括对象）都可以当做键，也就是说，Object结构提供了"字符串-值"的对应，Map结构提供了"值-值"的对应，是一种更完善的Hash结构的实现。如果你需要"键值对"的数据结构，Map比Object更合适。

```
var data1 = {a:1},data2 = {b:2},obj = {};

obj[data1] = 1;
obj[data2] = 2;

console.log(obj);// {[object Object]: 2}

console.log(data1.toString()===data2.toString());
//true;
```
 

 - 创建一个Map
```
const map = new Map([
 ['a',1],
 ['b',2]
]);
console.log(map);
//{"a" => 1, "b" => 2}
```

 - Map类的属性

    console.log(map.size)

 - Map类的方法

    ***1.set(key,value)设置键名key对应的键值为value，然后返回整个Map结构。如果key已经有值，则键值会被更新，否则就新生成该键。***
    ```
    map.set('miaov'.'ketang').set('new','fq').set('miaov','leo');
    
    console.log(map);
    //Map(4) {"a" => 1, "b" => 2, "miaov" => "leo", "new" => "fq"}
    ```
    ***2.get(key)get方法读取key对应的键值，如果找不到key，返回undefined***
    ```
    console.log(map.get('new'));
    //'fq'
    console.log(map.get('x'));
    //undefined
    ```
    ***3.delete(key)删除某个键，返回true，如果删除失败，返回false***
    ```
    console.log(map.delete('a'));
    //true
    console.log(map.delete('a'));
    //false
    ```
    ***4.has(key)某个键是否在Map对象中，如果是返回true，如果没有返回false***
    ```
    console.log(map.has('a'));
    //false
    console.log(map.has('miaov'));
    //true
    ```
     ***5.clear()清除所有数据，没有返回值***
     ***6.keys()返回键名的遍历器***
     ***7.value()返回键值的遍历器***
     ***8.entries()返回键值对的遍历器***
     ***9.forEach()使用回调函数遍历每个成员***

 - Map在使用中的注意事项：
 

    1.NaN 是相同的
    2.{ }是不同的
    3.特殊性质：数据是按照添加的顺序排列的
    ```
    {
      let s = new Map();
      s.set(2,2).set(1,1);
      
      // {2 => 2, 1 => 1}
    }
    ```

 ## 函数的默认参数
 

 - ES6允许给函数制定默认参数

```
function fn(a,b){
  a = a || 1;
  b = b || 2;
  
  console.log(a+b);
  }
  
  fn(); //3
  fn(0,1);  //2//出现问题
```

 - 添加默认参数
 
```
function fn2(a = 1,b =2){
  console.log(a+b);
}

fn2(); //3
fn2(0,1);  //1
```

 - 同样支持解构
 
```
function fn3({a,b}={a:1,b:2}){
  console.log(a+b);
}

fn3();  //3
fn3({});  //NaN

//------------------------
 function fn4({a=1,b=2}={}){
   console.log(a+b);
 }
 
 fn4();  //3
 fn4({});  //3
 fn4({a:4});  //6
```

## 函数的rest参数
 

 - es6中新增了rest参数，用来取代argumets，在est中废除了arguments  caller callee

```
// callee用法
(
  function(n){
    console.log(n);
    if(n===1) return n;
    return n*arguments.callee(n-1);
  }
)(3);

// caller用法
function f1(){
  console.log('我6666666！');
  setInterval(f1.caller,1000);
}

function f2(){
  console.log('6不6？');
  f1();
}

f2();
```
 
```
function add(...res){
 console.log(res);
  let ret = res.reduce(function (a,b){
    return a+b;
  });
  console.log(ret);
}

add(1,2,3,4);  //10
```

 - rest 参数 必须是最后一个参数
 
```
function fn(a=1,b=2,...res){
   console.log(a);
   console.log(b);
   console.log(res);
}

fn(); // 1 2 []
```

## 胖子函数

***胖子函数又叫箭头函数，通常用在函数表达式内和回调函数当中***

 1. 没有自己的this
 2. 没有arguments
 3. 不能当做构造函数

```
function add(a+b){
  return a+b;
}

const add = (a,b) => a+b;
//相当于 return a+b
console.log(add(1,2));  //3

const sortArr = arr => arr.sort();

console.log(sortArr([3,2,1]));
// [1, 2, 3]


const fn = (a = 1, b = 2) => {  //当有函数体的时候必须有 return
  console.log(a + b); //3
  return c = a + b + 2;
};
fn(); //5

const arr = [5,4,3,2,1];

arr.sort(function(a,b){
  return a-b;
})

arr.sort((a,b)=>a-b);
console.log(arr);
// [1,2,3,4,5]
```
 

 
 
 
 
 
     

 
    

 
 
 
    


    

 
