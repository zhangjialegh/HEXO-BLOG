---
title: DOM(文档对象模型)
data: 2017-3-06
tags: [js,DOM]
categories: js基础
---

##1、概念

 - DOM是针对XML的扩展，应用于HTML的应用程序编程接口API（为了能以编程的方法操作这个 HTML 的内容）。
 - DOM把整个应用程序界面映射为一个多层的节点结构，把这个HTML看做一个对象树（DOM树），它本身和里面的所有东西比如`<div></div>` 这些标签都看做一个对象，每个对象都叫做一个节点（node），节点可以理解为DOM 中所有 元素对象 的父类。
 

##2、节点属性
*节点至少有`nodeType`、`nodeName` 和 `nodeValue`这三个基本属性。节点类型不同，这三个属性的值也不相同*

---

 1*. 元素节点 `Node.ELEMENT_NODE(1)`
 2*. 属性节点 `Node.ATTRIBUTE_NODE(2)`
 3*. 文本节点 `Node.TEXT_NODE(3)`
 4. CDATA节点  `Node.CDATA_SECTION_NODE(4)`
 5. 实体引用名称节点 `Node.ENTRY_REFERENCE_NODE(5)`
 6. 实体名称节点 `Node.ENTITY_NODE(6)`
 7. 处理指令节点 `Node.PROCESSING_INSTRUCTION_NODE(7)`
 8*. 注释节点 `Node.COMMENT_NODE(8)`
 9*. 文档节点 `Node.DOCUMENT_NODE(9)`
 10. 文档类型节点 `Node.DOCUMENT_TYPE_NODE(10)`
 11. 文档片段节点 `Node.DOCUMENT_FRAGMENT_NODE(11)`
 12. DTD声明节点 `Node.NOTATION_NODE(12)`

  *1 2 3 8 9 是要记住的*

---
##3、childNodes
`ele.childNodes`可以获取到一个元素节点的所有子节点（包括换行符等文本节点和注释节点）*
##4、attributes

 - 通过`ele.attributes` 可以拿到ele元素属性节点的集合。
 - 例如：input元素，它的属性包括type、value等，就是这两个属性就是它的属性，而这两个属性称之为属性节点，属性节点就是属性节点本身，和这个input元素节点没有任何关系。

##5、parentNode/offsetParent

 -  `ele.parentNode`  可以获取ele的父节点 
 -  `ele.offsetParent` 可以获取到ele的定位的父节点

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
  <style>
    .offsetParent {
      width: 300px;
      height: 100px;
      border: 2px solid #000;
      position: relative;
    }
    .parent {
      width: 90%;
      height: 90%;
      background-color: pink;
      margin: 5px auto;
    }
    .child {
      position: absolute;
      right: 20px;
      top: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="offsetParent">
    <div class="parent">
      <span class="child">x</span>
    </div>
  </div>
  <script>
    var offsetParent = document.querySelector('.offsetParent');
    var parent = document.querySelector('parnet');
    var child = document.querySelector('.child');
    
    console.log(child.parentNode);
    console.log(child.offsetParent);
    
    child.onclick = function (){
      this.offsetParent.style.display = 'none';
    };
  </script>
</body>
</html>
```
##6、children

 - `ele.children` 获取到ele的所有元素的子节点，并且会动态的获取所有的元素。
 - 在DOM中几乎所有的方法都是动态的;
 - 不是动态的方法有：  
-document.getElementById("id");
   -document.querySelector('selector');
   -document.querySelectorAll('selector');

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
</head>
<body>
  <ul class="list">
    <!-- 注释节点 -->
    <li>1111</li>
    <li>1111</li>
    <li>1111</li>
    <li>1111</li>
  </ul>
  <ul class="list">
    <li>2222</li>
    <li>2222</li>
    <li>2222</li>
    <li>2222</li>
  </ul>
  <script>
    /**
     * 点击第一组的每个li变成红色，第二组的变成蓝色
     */
    var lists = document.querySelectorAll('.list');
    
    // var firstList = lists[0].getElementsByTagName('li');
    // var secondList = lists[1].getElementsByTagName('li');
    // 
    // for(var i=0; i<firstList.length; i++){
    //   firstList[i].onclick = function (){
    //     this.style.color = 'red';
    //   }
    // }
    // 
    // for(var i=0; i<secondList.length; i++){
    //   secondList[i].onclick = function (){
    //     this.style.color = 'blue';
    //   }
    // }
    // var firstList = lists[0].children;   
    // var secondList = lists[1].children;
    // 
    // console.log(Array.isArray(firstList));
    // 
    // console.log(firstList);
    
    // var lis = document.querySelectorAll('li');
    var lisTag = document.getElementsByTagName('li')
    
  
  </script>
</body>
</html>
```

##7、previousElementSibling/nextElementSibling

`previousElementSibling`获取到ele的上一个元素兄弟节点
`nextElementSibling` 可以获取到ele的下一个元素兄弟节点
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
  <style>
    .box {
      width: 400px;
      height: 200px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .box span {
      display: block;
      width: 100px;
      height: 100px;
      border: 2px solid #000;
    }
  </style>
</head>
<body>
  <div class="box">
    <span>111</span>
    <span class="target">222</span>
    <span>333</span>
  </div>
  <script>
    var target = document.querySelector('.target');
    
    target.previousElementSibling.style.backgroundColor = '#f88';
    
    target.nextElementSibling.style.backgroundColor = '#0f0';

  </script>
</body>
</html>
```
##8、firstElementChild/lastElementChild
`firstElementChild` 获取到ele的第一个元素子节点
`lastElementChild` 获取到ele的最后一个元素子节点
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
</head>
<body>
  <div class="box">
    <p>adasdsada</p>
    <p>adasdsada</p>
    <p>adasdsada</p>
  </div>
  <script>
    var box = document.querySelector('.box');
    
    box.firstElementChild.style.color = 'red';
    box.lastElementChild.style.color = 'blue';
    
  </script>
</body>
</html>
```
##9、表格的DOM操作
`table.tHead` 获取到表格头
`table.tFoot` 获取到表格脚

`table.tbody.rows[index]` 获取tbody里面的index行

`table.tBodies[0].rows` 获取到第一个tBody里面的所有的行

`table.tBodies[0].rows[0]` 获取到第一个tBody里面的第一行

`table.tBodies[0].rows[0].cells` 获取到rows[0]的所有单元格

`table.tBodies[0].rows[0].cells[1]` 获取到rows[0]的所有单元格中的第二个 

##10、DOM创建表格
`table.createThead()` 创建并返回创建的thead元素，然后自动插入table

`table.createTBody()` 创建并返回被创建的tbody元素，然后会自动插入
table

`table.createTFoot()`
创建并返回被创建的tfoot元素，然后自动插入table

`tbody.insertRow()` 向tbody中指定位置添加一行tr，并返回这个元素

`tr.insertCell()` 向tr中指定位置添加一个单元格td并返回这个元素

`table.deleteTHead()` 删除表格头

`table.deleteTFoot()` 删除表格脚

`table.tBodies[0].deleteRow()` 删除对应位置的行

`table.tBodies[0].rows[0].deleteCell()` 删除对应行的对应位置的单元格

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
</head>
<body>
  <table id="table"></table>
  <script>
    // 以下作为了解
    
    // 创建表格头  table.createTHead();  创建并返回被创建的thead元素，然后会自动插入table
    // var thead = table.createTHead();
    
    // 创建表格体 table.createTBody(); 创建并返回被创建的tbody元素，然后会自动插入table
    // table.createTBody();  
    
    // 创建表格脚 table.createTFoot(); 创建并返回被创建的tfoot元素，然后会自动插入table
    // table.createTFoot();
    
    // 通过 tbody.insertRow(_pos_); 向tbody中指定位置添加一行tr，并返回这个元素
    // 通过 tr.insertCell(_pos_); 向 tr中 指定位置 添加一个单元格 td 并返回这个元素
    
    // table.deleteTHead(); 删除表格头
    
    // table.deleteTFoot(); 删除表格脚
    
    // table.tNodes[_pos_].deleteRow(_pos_) 删除对应位置的行
    
    // table.tNodes[_pos_].rows[_pos_].deleteCell(_pos_) 删除对应行的对应位置的单元格
    
    var table = document.getElementById('table');
    
    console.log(table.createTHead());
    
    var tbody = table.createTBody();
    
    var tr = tbody.insertRow(0);
    tbody.insertRow(0);
    tbody.insertRow(0);
    
    tr.insertCell(0).innerHTML = '1111'
    tr.insertCell(1).innerHTML = '1111'
    tr.insertCell(2).innerHTML = '1111'
    tr.insertCell(3).innerHTML = '1111'
    
    tbody.insertRow(2).insertCell(0).innerHTML = '2222';
    
  </script>
</body>
</html>
```

##11、DOM操作表单

`document.forms` 获取到页面上的表单

`forms.someInputName` 获取到对应的name的表单内

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title></title>
</head>
<body>
  <form class="form1" action="index.html" method="post">
    <input type="text" name="text1" value="11111">
    <input type="submit" name="submit1" value="提交">
  </form>
  <form class="form2" action="index.html" method="post">
    <input type="text" name="text2" value="2222">
    <input type="submit" name="submit2" value="提交">
  </form>
  <script>
    // document.forms 获取到页面上所有的表单
    // froms.someInputName 获取到对应name的表单内部元素
    
    console.log(document.forms);
    
    console.log(document.forms[1]);
    
    console.log(document.forms[1].submit2);
    
  </script>
</body>
</html>
```