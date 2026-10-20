---
title: JavaScript 学习笔记
published: 2026-10-19
description: JavaScript 基础语法、数据类型、函数和常用概念整理。
tags: [JavaScript, 前端]
category: 前端
draft: false
---

# JavaScript

# 核心语法

- JS 用法，内链式和外链式

![](static/EAWFb20CHofx4Ixo1Y6cgcUrnge.png)

- **变量（Variable）**

  - `var num = 10`
- **数据类型（Types）**

  - number 数值类型： `var myNum = 10`
  - string 字符串类型：`var myStr = '文本' var myName = "吴悠" `
  - boolean 布尔类型：`var myBool = true`
  - null 类型，用于清空变量内容，表示空：`var myNull = null`
  - undefined 容器的默认值：`var myUn`
    ![](static/GFMsbtZ7FoQrCTx2M9McN5JUnBf.png)
- **运算符（Operator）**
  ![](static/SDqobyY2ZopNGwx375ZcNNsonfg.png)

  - 运算符优先级（从高到低）：
    ![](static/TGqCbe6GIoe42GxlurScLX3qnof.png)
- **语句（Statement）**

  - if 语句：
    ![](static/YYoqb6m44o9R8cx82szcSOEUnpg.png)
  - for 语句：
    ![](static/CeTlbNHV2o0Q6Yx1tORcL3yFnih.png)
- **函数（Function）**
  ![](static/TIAvbxjcZokOyLxYKxMcyns9nEb.png)
  ![](static/GpkvbFKgKoSka7xqzgbclW2EnJr.png)
- **数组（Array）**
  ![](static/HFOKbNwXgoJNOhxwWHDcTUMDnXd.png)

  - 遍历函数：数组.forEach()
    - 使用了闭包原理，function 里找不到 item 和 index 的的定义，会到上层作用域中（即 forEach 函数）中去寻找并使用
      ![](static/IM5Sb69JAo2O7MxdeFxc1UmcnpI.png)
  - 用到数组的其他方法可以去 mdn 上查
- **对象（Object）**

  - 和数组最大的区别是：对象是一种无序的数据存储方式，不再有索引
    ![](static/QL5eboS6VosKDOxQxdxc65SlnLd.png)
    ![](static/NWx1bH0QnoKJfExD1bfcAmann9e.png)

# DOM & Timer

基于浏览器提供的功能进行网页标签的操作

- DOM --- 文档对象模型（创建的 HTML 文档就是 document 对象）
- BOM --- 浏览器对象模型

## 元素操作（DOM Element）

- 通过 ID 获取元素：**document.getElementById()**

![](static/RzKAbimkNo4jFgxxKWpcMslyntd.png)

- 通过标签名获取：**document.getElementsByTagName()**
  ![](static/BWudbD4ZCoKMp0xeuP6cGGkUnpf.png)
- 按照选择器元素获取：**document.querySelectorAll()**

  - 标签
    ![](static/TzvebPne5oCgLgxfoFlcRNyInyg.png)
  - 类名
    ![](static/QR8EbgJ03o9oGAx1Alncmxvtnjb.png)
  - ID 里的标签
    ![](static/IjFEb8vSIoyOh8xdxSGcaiNJnGh.png)
- 按照选择器元素获取：**document.querySelector()**

  - 只会选出匹配到的第一个元素
  - 获取前一个同级的元素：**previousElementSibling**
  - 获取后一个同级的元素：**nextElementSibling**
    ![](static/E4A7byn0FoP7brxmzZVc3XntnBh.png)
  - 获取父级元素：**parentNode**
    ![](static/F70RbjwOqoe3ZfxPQQ2cLauan5g.png)
  - 获取子级元素：**children**
    ![](static/Qw5tbxXO0oH34JxPpsHcv2n2n7d.png)

## 样式处理（Style）

对元素进行样式的修改

![](static/BMxxbwp8DodlxcxHHWVcc6IpnOd.png)

一般情况下会新建一个类，只需要修改对象的类就能更改样式了

![](static/BxojbzD9woWJY3x6RkZc5t12n9c.png)

## 文本处理（Content）

- textContent 只能设置纯文本，innerHTML 则可以进行标签的生成

![](static/PgFdboiw8oS6RsxMkZMcbgI0n7c.png)

## 事件处理（Event）

![](static/C83lbyuRRo5cq3xxx3bcbccHnqg.png)

- onclick（会发生覆盖问题 --- 窗口只弹出一次）
  ![](static/FM6obNBweo6pPuxPjK8cX0GBnTd.png)
- addEventListener（较为常用 --- 窗口会弹出两次）
  ![](static/BF50bTqH4oDHDGxuS56cXnTcnbd.png)

  - 轮播图制作（定义一个新的类修改图象透明度）（小作业）
    ![](static/Ai1Nboew1ospCdxkcC5cZkFBnFc.png)

## 定时器（Timer）

- 延迟定时器：setTimeout（延迟指定时间后输出）
- 间隔定时器：setInterval（每间隔指定时间输出）

![](static/N4V7blmwkozVBjxJD6qcUjaynde.png)

- 六秒后停止输出（两种定时器结合使用）：
  ![](static/VUzMbaqxaovFxAxsmcPcc6Pqnlf.png)
- 由于 setInterval 只是隔段时间把任务放入队列中，并不是直接开始执行，因此会存在一定的延迟
- 使用 setTimeout 递归模拟 setInterval
  ![](static/MZH9biGf0o8nZYxs8tPc8msNnGd.png)

# ES6

## 变量和常量

- 变量 `let`

  - `var` 进行变量声明时可能不经意出现一些变量的覆盖，因此现在一般使用 `let` 进行声明
  - 除了普通代码块，还可以在代码中直接书写一个大括号表示独立作用域，作用域外无法使用里面声明的变量
- 常量 `const`

  - 声明不能修改的对象，取名方式一般全部大写加下划线，如 `const BASE_URL = 'http://wuyou.com'`

## 模板字符串

- 使用反引号结合 `${}`，能更方便快速连接字符串。里面也可以写 HTML 标签语法
  ![](static/Z9K2b4CX7otHddxD1jhcLrRKn2g.png)

## 标签模板

- 为每个占位符都增加 CSS 样式

![](static/BJc1bT0BEoskgPxbNX0cQBjanzc.png)

![](static/ZysVbgjmPoBXhrxqjAecoscHnJe.png)

## 解构赋值

- 适用于数组和对象两种类型
  - otherInfo 用来接收剩余项，只能放在最后（此处的...代表解构赋值功能）
    ![](static/J0zPbG2j6ojhWfxBKB1cURjonGd.png)

### 数组

- 使用结构表达式交换变量值，如 `[a, b, c] = [c, a, b]`
- 可以自动创建变量进行赋值，也可以使用默认值
  ![](static/Y3IpbPgYJoSZLcxG7xccUrPcnsd.png)
  ![](static/JrsZbP1hdobaoExqbalcuTvsn0d.png)
- 可以将中括号改为花括号，以属性的形式来指定元素的序号
  ![](static/VUvCbiY9to4GBGx4geFcDDvVnuK.png)
- 如果数组 arr 为空就会显示“数字为空”，如果不为空就会直接替换掉默认值
  ![](static/MZV2b9JVPoZA8oxVx2DcsHOhnuh.png)
- 把剩余值放在一个数组里，可以使用这个方法来进行整个数组的拷贝
  ![](static/KYiwb4bfqoSqbkxtCpJc1Ilnnxd.png)
  ![](static/GINQb2ZJboznCMxsI43cg9Yxnnb.png)
- 还能进行嵌套数组结构
  ![](static/IQ4Kbbe1ho9GTPx2sWQcr3FXnTh.png)

### 对象

![](static/H7SPbQdxSoxlg7xZlOMcxCOunjh.png)

- 对根本不存在的属性进行默认赋值
  ![](static/T1mIbc4cZoLV3UxZBY4c1D3Mnvd.png)
- 如果有两个属性不要，剩余的属性全都要，就可以这样操作
  ![](static/JJDibD5i7oAyZUxLoIFcHMKknNc.png)
- 用解构赋值的方法覆盖原来的变量值
  ![](static/Ck48bJ83toM1mmxArrMcWLLUnVd.png)
- 嵌套解构赋值
  ![](static/GCmxboGnhoBaU3xh77xc4YPVnyg.png)
- 遍历对象里的属性值
  ![](static/EDE8bU2nEoCMbKxsQ7ecTYRvnCb.png)

### 函数

- 对函数返回对象使用解构赋值

![](static/JhmgbNz4koZRiuxqXolc18WenDg.png)

### 字符串

- 取出字符串中的每一个字符

![](static/HBy6bbZLNoh014xDM9mcTLLwn0g.png)

- 给参数 item 加了个中括号，就变成获取每个元素后再获取字符串的第一个字符

![](static/Vb92by0W4oWurtxDYg4cmTmonAb.png)

### Map

- 想要获取 map 里键对应的值，可以通过这种方式省略掉键，获取所有值

![](static/HcnubOqXwouKFKxow9zcIiGjnsh.png)

### 模块

- 用来获取对应函数

```javascript
const { createServer } = require('http') // 或者
const { createServer: buildHttpServer } = require('http')
// 等价于
const http = require('http')
const createServer = http.createServer
```

### 正则表达式

![](static/KTaBbPllsoxGPIxdC9acIjANn5f.png)

## 数组和对象的扩展

- 扩展运算符

  - 数组（此处...的作用是将后面元素的所有键都展开）
    ![](static/NrypbUgZLoBmHpx5SDmcOon9nad.png)
  - 对象
    ![](static/Pckobw4xcoRcQuxce5ucu9rcnic.png)
- 数组方法

  - Array.from()：将伪数组转化为真实数组（arguments 本是个伪数组，forEach 是真实数组才能使用的方法）
    ![](static/RaXbb7YWio41aEx543ucVSqwn4g.png)
- 对象方法

  - Object.assign()：实现对象的浅拷贝、功能合并
    ![](static/MorYb9d6RohjkjxpkitcSs9cnhf.png)
    ![](static/GdGrbukONo0hqoxifwWcyPBwnre.png)

## Class 类操作

- 类的创建、初始化、方法
  ![](static/BASOb7prXoxuUyxkBxvcPvS1nrc.png)
- 类的继承（必须要先调用 super 方法）
  ![](static/PBsCbGsHJo4u7Jxe3cEc1g8dnid.png)

## 箭头函数

- 箭头函数是匿名函数的简写方式。正常匿名函数写法为

![](static/Cr32bOcO0oS0TXxPa9xcMZ3wnrd.png)

- 使用箭头函数方式简写
  ![](static/RYXWbWEEEo4MUGxNkaVcvuCHn8d.png)
- 箭头函数特点：
  ![](static/CJT8bb59AoKJWExlqkNch6OYnue.png)

  - 箭头函数不能用 new 来创建构造函数的实例，普通函数可以（因为箭头函数创建的时候程序不会为它创建 construct 方法，也就是没有构造能力，用完就丢掉了，不像普通函数重复利用，因此也不需要构造函数原型，也就是不会自动生成 prototype 属性）
  - 程序不会给箭头函数创建 arguments 对象，普通函数自身有
    ![](static/MT6pbJxdroon8ax7dTacUplcn5c.png)
    ![](static/ThFLbCZDUoV5W2xz7WJcbwNQnle.png)
  - 普通函数中的 this 是动态的，而箭头函数中的 this 指向的是紧紧包裹箭头函数的那个对象（定义时决定的），也就是说却决于外部普通函数的 this 值
  - 箭头函数不能通过 bind、call、apply 来改变 this 的值，但依然可以调用这几个方法（只是 this 的值不受这几个方法控制）
  - 箭头函数没有 super 和 new.target 绑定，和 arguments 一样，super 和 new.target 的值由最近那一层包围的普通函数所决定

## Promise 异步处理

- 常见的异步：定时器、Ajax
- 异步任务会在当前同步任务执行完毕之后再去触发

### Promise

- 用于解决异步写法中的嵌套问题，Promise 本身是一个类
  - resolve 表示成功，跳转到 then；reject 表示失败，跳转到 catch
    ![](static/UNVWbKT8KoFegHxtEAjcL0KYnPg.png)
  - 如果想给每个 then 失败跳转到不同结果的话如图所示。不想执行后面的 then 有两种处理方法，一种是返回一个新的失败状态的 Promise，另一种是抛异常
    ![](static/G8jcbhCWfo8s8QxadqHc1qZQnTh.png)
    ![](static/K9XUbLTkiosOYBx8bp6cKRxinub.png)

### Async

- 用来进行异步处理的语法糖，是一种基于 Promise 的异步操作简化
- 引擎在遇到 await 时，会等待直到 Promise 状态完成并返回结果
- 只需要按照同步任务的方法写，可读性强
- 唯一可能存在的嵌套是 reject 时会导致报错，可以给整体加一个 try catch 结构进行异常捕获操作
- 使用步骤：

  1. 准备一个返回 promise 对象的函数
  2. 为使用 await 的函数添加 async
- async 函数永远返回一个 Promise 对象

![](static/LPHibpLVwoiZdpxcKoZckys9nE8.png)

## Proxy 代理

- 设置成代理对象后，每次修改不仅能改值，还会进行额外的处理。
- 读取 `p1.name` → 触发 `get(target, property)`，`p1.name = 'jack'` 触发 `set`
- 下方代码中建议使用 `target` 替换函数中的 `obj`

![](static/KXlAboPl9oUkHgxL57nct4J7nDw.png)

## Module 模块

- 现在主流模块类型有两种：ESM（浏览器中） 和 CommonJS（Node.js 中）

### ESModule 使用方法

- 根模块中要加 `type="module"`
  ![](static/Y0sVbTMyfowsAQxhLBHcDIT2nAc.png)
- js 里面写 import
  ![](static/DytLbQgK6ojfSPxvncDckTUXn5F.png)
- a.js 和 控制台 中输出的结果如下（moduleA 是 a.js 里的 default 默认导出项）
  ![](static/BrSibMrmIocEsLxGR2McosuNnSc.png)
- 若要使用模块中的其他
  ![](static/CPpEbx5IDobfmNxJmahcI2fcnTb.png)

### CommonJS 使用方法

- c.js 的两种写法

![](static/PlQib1dVboCdqAxDNdncAklrnQb.png)

![](static/UynOblB09ovOobxLWFicUylon1e.png)

- 要通过 node.js 方式运行

![](static/Mf5kbIhQpob0YWxcN7gcFXDZnSh.png)

# Javascript 其他知识要点

## 相等（==）和全等（===）的区别

- == 会进行类型的转化，=== 不会进行

![](static/CH3EbILdXoypsDx2xeccEbKUn8f.png)

![](static/Rgo0bhFe7oQc0exFFW5cUBnLnOh.png)

- null 和 undefined 除了自身不等于任何的值，因此这两个在比较相等的时候不能转换为其他任何的值

![](static/BrlabyPbfoi515x5kfdcIJ6QnAb.png)

- NaN 意思是 Not a number，表示不是数字，表示非数字的一种状态，可以是一个范围里的任意一个数字，因此不等于自身

![](static/UROVb6pNqowXI4xyS05cskZunKe.png)

- 对于引用类型的对象，比较的是地址，而不是真实的值
  - 这里 ab 的对象分别保存在堆内存内的不同地方，而 ab 是保存在栈里面的内存地址
    ![](static/U5hwbLNuSo9RiexqwLIcWSaen9c.png)

## typeof 和 instanceof 的区别

![](static/FY2BbjpKnoiiPIxLuMCcgQuBnwe.png)

- typeof --- 一个用于检测数据类型的运算符，执行后返回一个小写的类型字符串

  - JavaScript 里的 简单数据类型：Undefined、Null、Boolean、Number、String，复杂数据类型：Object
  - NaN 归为 Number 类型
    ![](static/HKeNbVzy3o7Q1OxIBX2cLC9onTe.png)
- Instanceof --- 检测对象之间的关联性
  ![](static/Qp0BbD1YOoXA1Mxw7dQcxP5rnQO.png)

  - 左边的操作数一定要是引用类型值，不然的话，都会返回 false
    ![](static/PhMmbwOo0oH7RTx7aojcWdCGntc.png)
  - 左边返回一个实例的话则可以
    ![](static/E01ib0Q4vofGHHxhMorcaTa2nHh.png)

## document.write() 和 innerHTML 的区别

![](static/KUWibxiyGorvW9xyefkcFQvTn5c.png)

- document.write()

  - 可以在里面添加 HTML 表达式使用
  - window.onload 表示页面加载完之后的事件，document.write 会在页面加载完后将原本的内容覆盖掉，因此下面只会显示 script 中的内容
    ![](static/H47GblZKyornPpxTkbjcMXTPnab.png)
  - 如果在 js 文件中写入以下内容，只有把 script 标签放在最后时（第一种情况），文档中的内容会被覆盖掉，其他时候都不会覆盖
    ![](static/QDy9bqszxoaENYxqqKncQOjEnFe.png)
    ![](static/GHMZbru6jowe17xj7UecIA7JnGc.png)
  - 多次调用会将字符串内参数进行拼接
    ![](static/ShLrbYcdPo2kDNx1RE7cbOAmnAd.png)
- innerHTML

  - innerHTML 完整的写法为 element.innerHTML，使用方法：
    ![](static/GAGJb1zs2oVX8uxs0z7cPPHTn7b.png)

## 函数作用域

- 函数作用域，输出 apple

![](static/WD8NbONEbopMA7xyWR8cXCobnXg.png)

- 块级作用域：javascript 中 if 中定义的变量就会变成当前执行环境的变量
  ![](static/DpJHb1JXXotsMExCu0ZctiDxnvh.png)

  - 括号里面定义的变量不一定就是局部作用域
- 作用域链里的变量可以从里到外，不能从外到里

![](static/SCBxbNCzyoRheBxThMNcne3GnMe.png)

- 函数里面定义的变量会被提前声明

![](static/R0Nlb2YEsoVBzZxXqgQcHBbJnsf.png)

![](static/GRFDbSASiow7IGxgwtBcKTrNnyf.png)

- 函数里面定义的函数也会被提前声明
  ![](static/YS8Nb73Q2oUiXfx0rKAcc6r9nAc.png)
  ![](static/McaHb2VlGoEBISxIQNAc0ez9npe.png)

![](static/Ry98bJCVaowjAXx8AD7cEPjtnS7.png)

## 制作九九乘法表

![](static/MGAbbndpioegqfxsoJkcV5mbnlg.jpeg)

![](static/Rz1ybRevnojMvTxqhzOctY4MnQb.jpeg)

## 闭包

- 每当执行代码的时候代码就会生成执行上下文（执行环境），决定着代码的作用域。每次调用函数就会把该部分的上下文压入执行栈中
- 其实就是查找的时候沿着作用域链从里向外一层一层查找
- javascript 的执行环境分为：全局环境、局部环境和 Eval 环境
- 执行上下文

  - 创建阶段：创建作用域链（包含当前变量对象和所有父级变量对象）、变量对象（参数、变量、函数声明）、this
  - 执行阶段：变量赋值、函数引用等
- 会先执行同步任务再执行定时器异步任务

![](static/LMztbwBEgolxYax4KulcMTo0niv.jpeg)

- 改为立即执行任务后结果不同

![](static/RxfzbzGEiorVrcxtQI4ch8VLngf.jpeg)

## 原型对象

- 引用类型就是常说的对象

![](static/Rh6VborjEoWuPLxtobjcSRL2n6c.jpeg)

- 对象有个内置的属性“__proto__”，Number 对象也有自己的原型对象“Object”，

![](static/NovIbHjZyoaepqxhwk3cY2RqnMc.jpeg)

![](static/Y91ibQRSUoobBrx3eBVcj8EmnNe.jpeg)

- 所有对象最终都会指向原型“Object”

![](static/WM2HbLnIWohq3ox5HxIcBqUnnuc.jpeg)

![](static/O8mdbNgaroqlD8x3b7ZcbkJDnfg.jpeg)

？

## 原型链

![](static/QOZKbhuyuosUIBx46q8cDcQpnah.jpeg)

- f 只有方法 a，没有方法 b。f-F-Object

![](static/QyR6bjlkXoyUp6xWCYUcy96Dnff.jpeg)

- f → F.prototype → Object.prototype → null
- F

  - proto → Function.prototype
  - Function.prototype.__proto__ → Object.prototype
  - Object.prototype.__proto__ → null

![](static/Q7yKbpbJGoeBsjxCnbocZ4GLndW.jpeg)

## 事件捕获和事件冒泡

- DOM 事件流：自上而下捕获，到达目标，然后自下而上冒泡（上是最大的那个元素）

  - 事件捕获阶段
  - 处于目标阶段
  - 事件冒泡阶段
    ![](static/C9DLbzz0LoMH5mxQNXFc2MgOn7c.jpeg)
- 具体示例（冒泡传播）

![](static/Cg1Jb1qjso88wExjkYIcvfXQngb.jpeg)

- 对于 dom0 级 btn.onclick 和 dom2 级 btn.addEventListener('click',fn,false) 都是默认事件冒泡（自下而上）
  - 其中 dom2 级第三个默认 false，改为 true 就变为事件捕获。
    ![](static/KeYvbUweioL9GKx7qSTcfgwXn0b.jpeg)
    ![](static/R4STbse2NoL8uAxIUiCcyPNvnXg.jpeg)

## 小数精度问题

- javascript 采用 IEEE754 标准 64 位双精度，符号位 1 指数位 11 有效数位 52，因此表示小数时并不精确
- 解决方法：使用 toFixed 保留相应小数位，然后通过 parseFloat 将字符串转化为数字

![](static/HNZQbQhVkoFxmtxLGNkc1CaTn1g.jpeg)

## map() 和 parseInt()

- map()：只要传入一个函数，就会为函数附上对应的参数（item, index, array），并且执行函数
  - 这三个参数是数组本身的属性，即使不定义也会存在，选择是否使用

![](static/PwwUbyIMIoKsngxOdRmcCipkn5e.jpeg)

![](static/Icxtbhwd6oJhfAxAy8ecMGvHnUg.jpeg)

- parseInt()

  - 在括号里输入字符串，把字符串里的数字提取出来
  - 也可以设置第二个参数，表示第一个参数的进制
    - 0: 十进制
    - 2-36: 对应进制
    - 小于 2 或大于 36: NaN
- 面试题
  ![](static/WuzTb2D5po6FY1xJBs1c1JWHnYO.jpeg)

  - map 会自动传入三个参数，而 parseInt 只用到了两个参数
    ![](static/NRSpb55xFoqYODxhulbcf8IznMf.jpeg)

## var let 和 const 的区别

![](static/DsQob2sutoy3u2xTUcqcQy6qneb.jpeg)

1. const let 是块级作用域（for if 之类的也是块级作用域），var 没有块级作用域，var 只有函数和全局作用域
2. const let 不存在变量声明的提前，var 有声明的提前，所以 const 和 let 在声明变量/常量 之前，是没办法获取到的，称为暂时性死区 temporal dead zone
3. const let 是 ES6 提出的，var 是 ES5
4. const 声明的是常量，常量不能被修改（但是如果是指针的话，地址指向的内容可以修改），let 和 var 声明的是变量，可以被修改
5. const 在声明时必须赋值，而 let 和 var 不需要
6. let 和 const 不能重复声明同一个值:如 let a=1 ; let a =2 这样是不被允许的，但 var 可以，最后一个 var 声明的值会覆盖之前的 如：var b =1 ;var b =2 console.log(b)  结果为 2

- onmouseover 回调函数属于宏任务，是异步任务。使用 var 没有形成块级作用域，因此所有 i 都会显示 5。将 var 改为 let 即可实现期望效果

![](static/W80Wbv6agobb4jxRn4Oc3wcEndh.jpeg)

## 拖拽功能

- 方法一：draggable = "true"
  ![](static/Gxtgb4w6aoskRjxWXOxcKP3Yn7c.png)

  - 将右侧图片拖动到左边
    ![](static/BgiIbjg2yonM18x8HzZcueEKndb.png)
    ![](static/EDanb8ZL3oefBVxOgDPcQEKVntf.png)
  - 浏览器默认不能在拖拽行为后进行放置，因此取消默认行为（dragover 部分代码）
  - 如果空元素有节点了就去除掉（dragenter 部分添加的代码）
    ![](static/Joo9bW7hyoJ7CGxD5GucfBJVngh.png)
- 方法二：鼠标事件 --- 对元素进行绝对定位后修改 left 和 top 值

  - 鼠标按下：mousedown
  - 鼠标移动：mousemove
  - 鼠标松开：mouseup
    ![](static/IxZhb1b3Wo4EBOxEP1Dc2KHonRe.png)

![](static/ZqLRbmzxOonAaXxkmivc6YagnPf.png)

## 实现 call、apply 和 bind 啊啊啊啊啊啊啊？

- this 指向上一级对象（隐式绑定）

![](static/Ri2lby6IooNlmmxtMDWcPASen4b.png)

![](static/ZKv6bLQPLovS1MxCrRBcltnenDn.png)

- call 用来修改 this 指向

![](static/WpB5b83xGo7juqxd0nEcGUZxnub.png)

- apply
- bind

## 函数柯里化

- 函数柯里化：把接收多个参数的函数，拆解成一系列只接收单个参数的嵌套函数
- 作用：

  - 对函数参数复用的情况进行优化
    ![](static/IYIgbQ7eFoXKOJxy024czzfinDd.png)
  - 对浏览器兼容性进行检测：提前判断有些函数和方法是否被浏览器支持（如 addEventListener、attachEvent），使用立即执行函数进行编写
    ![](static/Lo2QbMhimoNfefxaCEfcMzinnB2.png)
    - element 就表示哪个元素需要添加事件监听
    - type 就是元素需要添加什么类型的事件
    - listener 就是执行的回调函数
    - useCapture 就是要进行事件冒泡或者事件捕获的选择
    - 另外为了规避掉 this 指向问题，这里用 call 进行 this 的绑定，并且把原来函数里面隐藏的 event 对象代入的参数里面
    - 使用方法：

    ```javascript
    ```

// 给按钮绑定点击事件
const btn = document.getElementById('btn');
whichEvent(btn, 'click', function(e){
console.log(this); // this 是 btn 元素
console.log(e); // 事件对象
})

```
	- 延迟执行
		![](static/YTVMbHWreoRnS3xbmyacBV3mn5G.png)
		![](static/JNGIb16qPoR9UnxgsegcjRXDn9f.png)
		- `Array.prototype.slice.call(arguments)`：把类数组 arguments 转为真正数组
		- `reduce`：遍历数组，持续累积计算，最终返回一个最终值（求和、求积、拼接、统计、转对象都能用）
	- 柯里化箭头函数
		- 如果有很多个不同的数组，里面对象的键值对名字不一样，想要获取数组里面的名字，使用柯里化进行参数复用
		![](static/X5Bsbr5Zso8gGGxupYhcMWexnyb.png)

## defer 和 async 的区别

![](static/ZnAFbr0ZJoTMawxwX5mclyZQnrd.png)

![](static/NhzYbIjpMoZQVdx1G9icapiUnpH.png)

- **async**：异步加载
	- 页面加载时，带有 async 的脚本也同时加载，加载后会立即执行，如果有一些需要操作 [DOM](https://search.bilibili.com/all?from_source=webcommentline_search&keyword=DOM&seid=5514259679849423240&from_avid=330795664&from_comid=3876645097&search_half_screen=1&half_screen_page_type=1&scroll_to_fullscreen=1) 的脚本加载比较慢时，这样会造成 DOM 还没有加载好，脚本就进行操作，会造成错误
	- 比较适合一些第三方脚本

- **defer**：推迟加载
	- 页面加载时，带有 defer 的脚本也同时加载，加载后会等待 页面加载好后，才执行
	- 比较适合一些与DOM有关联的脚本

## Symbol类型

![](static/Gn2tbyCi5oNBTvxiGCccpx7anCe.png)

- Symbol类型是原始值，不是引用类型，无法继承属性，不能new Symbol

- 用Symbol类型，使用别的函数无法访问，除非是Object.getOwnPropertySymbols()

![](static/D9vObj2MaoTC2xxwK6uchBLun2d.png)

- 使用Symbol.for设置母亲

![](static/Jv1ObQcXDorzFNxY8jhc7vVYn7g.png)

- 特点总结：
	1. Symbol函数接受一个可选参数，方便代码阅读和后期调试
	2. 用Object.getOwnPropertyNames(), Object.keys()或者for...in等方法无法显示Symbol属性名
	3. Object.getOwnPropertySymbols()方法返回包含所有Symbol属性的数组
	4. Symbol函数不能使用new，因为是原始值
	5. Symbol.for()创建共享Symbol，如果已存在，直接返回已有的Symbol
	6. Symbol函数创建的原始值都是唯一的
	7. Symbol.keyFor()返回已登记Symbol有关的键

## 防抖

- 防抖是规定时间内发生抖动时不执行后续操作

- 对按钮进行防抖设置：用户在短时间间隔内多次按下按钮，只在最后一次生效

![](static/B4FQbjHfYoZPulxQSdBc9leRn9e.png)

## 节流

- 节流指规定时间间隔内后续动作只会执行一次

- setTimeout() 方法：在时间间隔内就取消执行

![](static/PwRHb8R1KoJlQjxOstPcilTpnJd.png)

- Date() 方法：记录上次执行的之间点，超出时间间隔才执行

![](static/HKo9b0UcEombFWxUBGvcmPrxnJX.png)

## 创建对象的多种方法

- New Object()
	![](static/PEJIbZ0E7o3pFmx2mkDcMOKpnb8.png)

- 对象字面量
	![](static/Q0fxboKJ5ovBXTxMutAcG47in2c.png)

- 工厂模式：解决了创建多个类似结构对象的问题（不会把对象和建造函数进行关联）

![](static/JQOgbBx0ZoDQCBxTxsHciUFUnnb.png)

- 构造函数：会把对象和构造函数进行关联

![](static/DpX7bwoTTohNbfxIH1dcIQxfnhd.png)

- Object.create()：利用原有对象进行新对象的创建，对新对象进行修改原型对象也会被修改
	![](static/VoJfblJR3op5WOxfiaocirYpn9b.png)

- class：融合了构造函数和原型
	![](static/Omz1bRbLeoSYINxnMjWc2S9Xn8b.png)

## 宏任务与微任务

- javascript是单线程的，也就是只有一个调用栈，先入后出，一次一个，可以嵌套

- 执行调用栈会先执行同步任务，发现异步任务时会将其放入队列中

- 异步任务分为宏任务队列和微任务队列，先进先出
	- 注意并不是每个浏览器都把这些函数归为同一类宏任务或微任务，有些浏览器会把Promise.then归为宏任务
	- 宏任务
		- 新程序或子程序被直接执行（比如<script>元素里面运行的代码就是程序被执行）
		- 事件的回调函数（比如鼠标点击事件）
		- setTimeout()和setInterval()
		- requestAnimationFrame，I/O操作，setImmediate，UI rendering等等
	- 微任务
		- Promise .then() .catch() .finally()
		- MutationObserver
		- Object.observe
		- Node.js里面的process.nextTick()

- 执行顺序：靠Event Loop事件循环
	- 执行完同步任务后，执行微任务队列里的任务，最后执行宏任务
	- 每次宏任务结束后也会优先执行微任务，直到微任务队列全部清空才执行下一轮宏任务

## 图片懒加载

- 图片懒加载就是延迟加载
	- 网页比较长用户看不到下面的图片，等用户滚动鼠标才加载下方本来看不见的图片

- 方法一：事件监听（scroll）
	- 如果图片可以看见，则图片距离视窗顶部的距离小于窗口显示区的高度，反之大于
	- 使用自定义属性使浏览器一开始不加载这些图片（将“src”改为“data-src”）
	- 但是这种方法滚动事件被触发了很多次，可能导致任务的堆积，而且不断触发事件很消耗资源
	![](static/P3nDbVJ5GoJWavxXJricDIi1nbL.png)

- 方法二：IntersectionObserver
	- 是浏览器提供的构造函数，会观察目标元素和可视窗口产生的交叉区域
	![](static/WnNgbKjXMoWdtmx5ItFc5wknnVh.png)

## Ajax

- 用来刷新页面，而不用刷新整个网页

```
