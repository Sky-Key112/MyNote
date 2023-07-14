# ES
ES6是 JavaScript的最新标准
旧标准为ES5 
可以使用`Babel 转码器`转码为旧标准用法的环境

## 变量

`var`全局变量
`let`局部变量 （同区块内可用）
`const`只读常量
1. 变量提升：`var`声明在使用后边，会自动提升，既编译时就定义为`undefined`在var赋值后再为对应值;`let`不存在变量提升，在使用之后定义会直接报错。

变量的区块
1. 每一对`{}`内,都算一个区块,在区块中声明的变量,不会影响外部的区块。
2. 区块之间可以嵌套

## 顶层对象

`JavaScript` 语言存在一个顶层对象，它提供全局环境（即全局作用域），所有代码都是在这个环境中运行。但是，顶层对象在各种实现里面是不统一的。
- `浏览器`里面，顶层对象是`window`，但 `Node` 和 `Web Worker` 没有`window`。
- `浏览器`和 `Web Worker` 里面，`self`也指向顶层对象，但是 `Node` 没有`self`。
- `Node` 里面，顶层对象是`global`，但其他环境都不支持。
```js
var a = 1;
// 如果在 Node 的 REPL 环境，可以写成 global.a
// 或者采用通用方法，写成 this.a
window.a // 1

let b = 1;
window.b // undefined
```

`ES2020`在语言标准的层面，引入`globalThis`作为顶层对象。也就是说，任何环境下，`globalThis`都是存在的，都可以从它拿到顶层对象，指向全局环境下的this。

可以直接使用`globalThis.a`获取到变量a的值。

## 赋值 
