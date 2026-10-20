---
title: TypeScript 学习笔记
published: 2026-10-19
description: TypeScript 类型系统和开发实践整理。
tags: [TypeScript, JavaScript, 前端]
category: 前端
draft: false
---

# TypeScript

# 核心基础

## 常用操作方式

- 类型推断：TypeScript 会根据给变量存放的初始值类型推断，进行变量类型限定
- 类型注解：书写的时候主动对类型进行注解

  ```javascript
  ```

let str:string = 'abc'

```

- 类型断言：人工干预断言值是某个类型
	- 由于第二行可能没有值，不加 as number 会报错
	- 如果确认里面必然有值大于2，加上as number 进行人工干预
	```javascript
let numArr = [1, 2, 3]
const result = numArr.find(item => item > 2) as number
result * 5
```

## 基础类型和联合类型

```typescript
let v1: string = 'abc' // 基本类型
let v2: number = 10
let v3: boolean = true
let nu: null = null
let un: undefined = undefined
    
let v4: string | null = null  // 联合类型，表示有可能被分配两种类型
// null 和 undefined 默认可以被分配给其他任意类型
// 一旦开启 strictNullChecks 配置项，就不能将 null 和 undefined 随意分配给其他类型，需要第7行这种写法
let v5: 1 | 2 | 3 = 2
```

## 数组、元组、枚举

- 数组类型

```javascript
let arr: number[] = [1, 2, 3]                    // 方式一
let arr1: Array<string> = ['a', 'b', 'c']        // 方式二
```

- 元组类型

```javascript
let t1: [number, string, number?] = [1, 'a']   // ? 表示第三个值是可选的（可以不写）
```

- 枚举类型

```javascript
enum MyEnum {
    A,
    B,
    C
}
console.log(MyEnum.A)   // 使用方式一
console.log(MyEnum[0])  // 使用方式二
```

- void 类型
  - 使用的时候 void 只能被分配 undefined 值，通常用于给函数赋值，表示没有返回值

## 函数

```typescript
function MyFn (a = 10, b: string, c?: string, ...rest: number[]): number {  
// 添加？为可选参数，可选参数要在必选参数（如果像 a 添加一个默认值的话，可以在必选参数左侧）
    return 100
}
const f = MyFn(20, 'abc', true, 1, 2, 3)
```

## 接口 interface

- 通常用来进行一个对象的定义（对对象的数据类型进行定义）

```typescript
interface Obj {
    name: string,
    age: number
}
const obj1: Obj = {
    name: 'a',
    age: 10
}
```

## 类型别名 type

```typescript
type MyUserName = string | number
let a: MyUserName = 10
```

## 泛型 T

- 相当于 C++ 中的模板

```typescript
function myFn<T>(a: T, b: T): T[] {
    return [a, b]
}
myFn<number>(1, 2)
myFn('a', 'b')  // 自动类型推断
```

# 进阶内容

## 函数重载

- JavaScript 里面不支持
- 函数重载：创建多个名称一样，参数类型和返回值不同的函数

```typescript
function hello (name: string): string
function hello (age: number): string
function hello (value: string | number): string {
    if (typeof value === 'string') {
        return '你好，我的名字是'+ value
    } else if (typeof value === 'number') {
        return `你好，我的年龄是${value}`
    } else {
        return '非法格式'
    }
}    
hello('abc')
hello(18)
```

## 接口继承 extends

- 使用接口继承可以将接口的功能进行更好的复用

```typescript
interface Parent {
    prop1: string
    prop2: number
}
interface Child extends Parent {
    prop3: string
}
const myObj: Child = {
    prop1: '',
    prop2: 1,
    prop3: ''
}
```

## 类的修饰符 public static readonly

```typescript
class Article {
    public title: string
    content: string                 // 默认为 public
    aaa?: string                    // 可选属性
    bbb = 100                       // 默认值为 100
    
    private tempData?: string       // 只能在类的内部进行访问
    protected innerData? : string   // 只能在当前类内部和子类中进行访问
    
    static author: string           // 静态属性 static
    private static readonly year: number = 1997 // 只读 read only，设置完后不能修改
    
    constructor (title: string, content: string) {   // 构造函数
        this.title = title
        this.content = content
    }
}

const a = new Article('标题', '内容')
Article.author = 'asd'    // 静态属性设置给类本身，而不是设置给类的实例

class B extends Article {
    constructor (title: string, content: string) {
        super(title, content)
        this.innerData   // 子类可以访问父类中的 protected 属性
    }
}
```

## 存取器 get set

- 使用户能够从外部修改类中的私有属性

```typescript
class User {
    private _password: string = ''
    get password(): string {  // 访问 password 时返回
        return '******'
    }
    set password(newPass: string) {  // 设置 password 时进行操作
        this._password = newPass
    }
}

const u = new User()
console.log(u.password)
```

## 抽象类 abstract

- 抽象类是一种基类，使用其派生出很多子类进行使用，相当于一个规范作用

```typescript
abstract class Animal {
    abstract name: string        // 抽象属性，在子类中必须被覆盖
    abstract maskSound(): void   // 抽象函数
    move (): void {              // 普通函数， 在子类中将直接被继承
        console.log('移动')
    }
}

class Cat extends Animal {
    name: string = '小猫'
    maskSound(): void {
    
    }
}
```

## 类实现接口 implements

- 也就是用接口去给类的创建提供一个规则
- 可以用类实现多个接口，类里需要覆盖接口里所有属性和函数
- 解决了不能同时继承多个类的问题

```typescript
interface Animal {
    name: string
    get sound(): string
    makeSound(): void
}
interface B {
    age: number
}
class Dog implements Animal, B {
    name: string = '小狗'
    age: number = 10
    get sound() {
        return ''
    }
    makeSound(): void {
    
    }
}
```

## 泛型类 T

```typescript
class MyClass<T> {
    public value: T
    constructor (value: T){
        this.value = value
    }
    do (input: T): T {
        console.log('处理数据', this.value)
        return input
    }                                    
}

const myStr = new MyClass<string>('hello')
myStr.do('abwadw')

const myNum = new MyClass<number>(123)
myNum.do(456)
```
