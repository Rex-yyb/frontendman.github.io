# ES5基础

## 基础概念

* 表达式(expression)：执行后能够最终返回一个值，比如
  * `a + b`
  * `x === 1 ? true : false`
  * `func(1,2)`
* 语句(statement)：通常是执行某个操作，表达式可以是一个语句(expression statement)也可以是语句的一部分。比如
  * `let result = x === 1 ? true : false`
* 字面量(literal)：也被称为直接量，是指声明一个变量时，它的值是一个常量，比如
  * `let a = 1`
  * `let animal = ["lion","angle"]`
  * `let per = { name: "liming", age: 10 }`

## 数据类型

| 类型      | 说明                                          |
| --------- | --------------------------------------------- |
| undefined | 没有定义或者没有设置值的变量                  |
| boolean   |
| number    | 普通数值、NaN、Inifinity都是number类型        |
| string    |
| object    | 普通对象、数组等都是object类型                |
| null      | 一个表明 null 值的特殊关键字                  |
| symbol    | ES6中新增，一种实例是唯一且不可改变的数据类型 |

```js
let undef
typeof (undef)//undefined
typeof (0)//number
typeof (NaN)//number
typeof (Infinity)//number
typeof ("")//string
typeof (true)//boolean
typeof ({})//object
typeof ([])//object
typeof (null)//object
```
## 作用域(Scope)

作用域指的是代码运行时的变量、函数和对象的可访问性。换句话说，作用域决定了代码区域中变量和其他资源的可见性。

JS采用的是[Lexical Scope](https://stackoverflow.com/questions/1047454/what-is-lexical-scope) (Static Scope)。代码所在位置决定了它的作用域链。嵌套的代码块可以访问到它的父作用域，并且优先从当前作用域往父作用域查找(variable shadow)。作用域可以在编译时推导，并且符合人的阅读习惯。与之对应的是Dynamic Scope，它作用域是动态的，依赖于函数的链调用。


``` javascript
function grandfather() {
    let name = 'Hammad';
    // likes is not accessible here
    function parent() {
        // name is accessible here
        // likes is not accessible here
        function child() {
            // Innermost level of the scope chain
            // name is also accessible here
            let likes = 'Coding';
        }
    }
}
// name is not accessible here
```

#### Global Scope
全局作用域中的变量可以从应用程序的任何地方访问。直接使用`<script>`标签加载的JavaScript文件或代码的最外层作用域内定义的变量。可直接通过`变量名`进行访问。

?> 使用let和const定义的全局变量，无法通过`window.`进行访问。在Chrome Devtool中被let和const定义的全局变量，被定义为`Script Scope`

``` html
<script>
    // "global" scope
    var x = 1
    let y = 2
    const z = 3
</script>

<script>
    console.log(x)//1
    console.log(y)//2
    console.log(z)//3
    console.log(window.x)//1
    console.log(window.y)//undefined
    console.log(window.z)//undefined
</script>
```

#### Module Scope
ES2015引入了一个模块作用域，在该模块内定义的内容，无法被外部模块直接访问。

``` html
<script type="module">
    // "Module" scope
    let x = 1
    var y = 2
    const z = 3
</script>

<script>
    console.log(x)//Uncaught ReferenceError
    console.log(y)//Uncaught ReferenceError
    console.log(z)//Uncaught ReferenceError
</script>
```

#### Function Scope

在函数中定义的参数和变量在函数内的任何地方都是可见的，但在函数外不可见。

``` javascript
function demo(){
    //"Function" scope
    let x = 1
    var y = 2
    const z = 3
    console.log(x)//1
    console.log(y)//2
    console.log(z)//3
}

console.log(x)//Uncaught ReferenceError
console.log(y)//Uncaught ReferenceError
console.log(z)//Uncaught ReferenceError

```

#### Block Scope

当你在一个代码块(`{}`)中使用`const`或`let`声明一个变量时，你只能在该代码块中访问这个变量。需要注意的是：使用`var`定义的变量不存在块级作用域（定义提升）。这也是为什么我们提倡使用`let`和`const`替代`var`的重要原因

``` javascript
if (true) {
    var x = 1
    //"Block" Scope
    let y = 1
    const z = 1
}
console.log(x) // note: visible outside the block
console.log(y) // Uncaught ReferenceError 
console.log(z) // Uncaught ReferenceError 
```

``` javascript
for(var x = 0; x < 5; ++x) {
    //do something
}
console.log(x) // note: visible outside the loop

for(let x = 0; x < 5; ++x) {
    //do something
}
console.log(x) // Uncaught ReferenceError
```

## 闭包(Closure)

当前一个函数引用了函数外部的变量时，这就创建了一个闭包。

比如下面的例子，`innerFunc`和它引用的变量组合而成的整体就是一个闭包，`outerVar`就是闭包引用

``` js
function outerFunc() {
  let outerVar = 'I am outside!';

  function innerFunc() {
    console.log(outerVar); // => logs "I am outside!"
  }
}
```

以下是对于闭包的特殊使用场景的介绍

#### 创建私有变量

``` js
let demo = (() => {
  let count = 0

  return {
      increase:()=>{
          count++
      },
      decrease:()=>{
          count--
      },
      getCount(){
          return count
      }
  }
})()

demo.increse()
demo.getCount()//1
demo.decease()
demo.getCount()//0

```
#### 创建函数(函数工厂)

典型的场景就是函数式编程的柯里化（Curry）

``` js
function multiply(a) {
  return function executeMultiply(b) {
    return a * b;
  }
}

const double = multiply(2);
double(3); // => 6
double(5); // => 10

const triple = multiply(3);
triple(4); // => 12
```
## 执行上下文


## this


#### 通过 call、apply和bind改变this


## 原型链v

## 参考资料

* [语法和类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Grammar_and_types)
* [A Simple Explanation of JavaScript Closures](https://dmitripavlutin.com/simple-explanation-of-javascript-closures/#4-the-closure)
* [A Simple Explanation of Scope in JavaScript](https://dmitripavlutin.com/javascript-scope/#5-scopes-can-be-nested)
* [An introduction to scope in JavaScript](https://www.freecodecamp.org/news/an-introduction-to-scope-in-javascript-cbd957022652/)
* [What is the scope of variables in JavaScript?](https://stackoverflow.com/questions/500431/what-is-the-scope-of-variables-in-javascript)
* [You Don't Know JS Yet (book series) - 2nd Edition](https://github.com/getify/You-Dont-Know-JS)
* [JavaScript Scope and Closures](https://css-tricks.com/javascript-scope-closures/)
* [JavaScript: var, let, const](https://dev.to/sandy8111112004/javascript-var-let-const-41he)
* [Understanding Scope in JavaScript](https://scotch.io/tutorials/understanding-scope-in-javascript#toc-lexical-scope)
* [what-is-the-execution-context-stack-in-javascript](https://medium.com/@itIsMadhavan/what-is-the-execution-context-stack-in-javascript-e169812e851a)
* [Understanding Javascript ‘this’ keyword (Context)](https://towardsdatascience.com/javascript-context-this-keyword-9a78a19d5786)