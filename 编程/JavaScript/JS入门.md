# 入门建议

1. `了解基础语法` - 学习变量、数据类型、运算符、条件语句、循环等基础语法。可以通过在线教程或书籍学习。

2. `学习DOM操作` - DOM(文档对象模型)允许你通过JavaScript来操作网页。学习如何通过JavaScript来选取、添加、删除、修改网页元素。

3. `学习事件绑定` - 学会给元素绑定点击、鼠标移入等事件,使网页能够响应用户交互。

4. `学习Ajax请求` - Ajax请求允许网页异步获取数据而不需要刷新。可以用于给网页添加动态内容。

5. `学习JQuery库` - JQuery是最流行的JavaScript库,可以简化DOM操作、事件绑定等过程。

6. `练习小项目` - 通过一些简单的项目练习JavaScript,如图片滑动、时钟、计算器等。

7. `了解前端框架` - 后期可以学习一些流行的前端框架如React、Vue、Angular等。

8. `掌握调试技巧` - 学习使用浏览器调试工具、console等来调试JavaScript代码。

9. `多写多练` - 编写更多代码并不断练习,这是掌握JavaScript的最好方式。

# 基础语法
JavaScript的基础语法包括以下几个方面:

1. `变量` - 使用 var、let、const 来声明变量,可以存储数据。

2. `数据类型` - 主要包含 Number、String、Boolean、Object、Array等类型。

3. `运算符` - 算数运算符 + - * / %等,比较运算符 == === > <等,逻辑运算符 && || ! 等。

4. `函数` - 使用`function`关键字定义函数,可以封装功能代码。

5. `条件语句` - 使用if、else if、 else 来执行条件代码块。

6. `循环语句` - for循环、while循环、do while循环来重复执行代码块。 

7. `事件` - 可以检测用户交互,如click点击、mouseover鼠标移入等。

8. `对象` - 使用对象literal `{ }`来创建对象,对象包含属性和方法。

9. `数组` - 使用 `[]`来创建数组,可以存储数据列表。

10. `DOM操作` - 用来操作HTML文档,如获取元素、添加节点、修改内容等。

11. `BOM操作` - 用来操作浏览器,如弹窗、控制URL等。

# DOM与BOM操作
DOM 操作是指用 JavaScript 来操作 HTML DOM (`Document Object Model`),也就是网页的文档对象模型。通过 DOM 接口可以让JavaScript获取页面元素并对元素进行操作。

常见的 DOM 操作包括:

- 获取元素:通过 id、标签名、类名等选择元素,如 `getElementById`、`getElementsByTagName` 等。

- 修改元素:改变元素的内容、属性、样式等,如 `innerHTML`、`setAttribute`、`style` 等。

- 创建元素:创建新节点,如 `createElement`、`appendChild` 等。

- 删除元素:从 DOM 中删除元素,如 `removeChild` 等。

- 事件:给元素绑定各种交互事件,如 `click`、`mouseover` 等。

BOM 操作指的是用 JavaScript 来操作浏览器,主要对象包括:

- `window`:浏览器窗口对象。

- `location`:浏览器地址栏信息。

- `navigator`:浏览器信息。

- `screen`:用户屏幕信息。

- `history`:浏览器历史记录。

常见的 BOM 操作有:

- 弹出框:`alert、confirm、prompt` 等。 

- 打开关闭窗口:`open、close` 等。

- 获取浏览器信息:`navigator` 对象。

- 操作浏览器历史记录:`back、forward、go` 等。

- 定位对象:`location` 对象。

# 事件
JavaScript中的常用事件主要有以下几种:
1. `onclick` 点击事件 - 当用户点击元素时触发。

2. `onload` 加载完成事件 - 当页面或图像加载完成时触发。

3. `onmouseover` 鼠标移入事件 - 当鼠标移入元素时触发。 

4. `onmouseout` 鼠标移出事件 - 当鼠标从元素移开时触发。

5. `onkeydown` 键盘按下事件 - 当按下键盘按键时触发。

6. `onkeyup` 键盘弹起事件 - 当松开键盘按键时触发。

7. `onsubmit` 表单提交事件 - 当提交表单时触发。

8. `onfocus` 获取焦点事件 - 当元素获得焦点时触发。

9. `onblur` 失去焦点事件 - 当元素失去焦点时触发。

10. `onchange` 内容改变事件 - 当元素内容改变时触发。

其中最常用的事件是:

- `onclick` - 处理点击事件,如按钮点击。
- `onload` - 在页面加载完成后执行代码。
- `onmouseover`/`onmouseout` - 处理鼠标移入/移出元素事件。
- `onkeydown`/`onkeyup` - 响应键盘输入。
- `onsubmit` - 在表单提交前验证或处理数据。

## 绑定
1. 在HTML元素中直接绑定

```html
<button onclick="handleClick()">Click Me</button>
```

2. 使用元素的事件属性

```js
var btn = document.querySelector('button');
btn.onclick = function() {
  // 处理点击事件
}
```

1. 使用`addEventListener()`方法 ***(推荐使用)***

```js
var btn = document.querySelector('button');
btn.addEventListener('click', function() {
  // 处理点击事件 
});
```

addEventListener()的优点是`可以添加多个事件监听器,按注册顺序触发`。
addEventListener()遵循W3C标准,事件名`不加前缀on`

1. 使用attachEvent()方法(IE低版本支持)

```js
var btn = document.querySelector('button'); 
btn.attachEvent('onclick', function() {
  // 处理点击事件
});
```

# AJAX请求
AJAX 请求只能请求与页面同源(`同协议、域名、端口`)的接口或资源。

AJAX(Asynchronous JavaScript and XML)即异步JavaScript和XML,可以实现无需重新加载页面的情况下请求服务器的数据。其基本工作原理如下:

1. 创建XMLHttpRequest对象,即创建一个异步请求对象:

```js
var xhr = new XMLHttpRequest();
```

2. 设置请求方法和请求URL:

```js
xhr.open('GET','/data.json');
```

3. 发送请求:

```js
xhr.send(); 
```

4. 注册事件回调,处理请求结果:

```js
xhr.onload = function(){
  // 在这里处理返回数据
}
```

5. 在回调函数中可以通过xhr对象的response属性获取到服务器返回的数据。

使用AJAX的优点:

- 提高用户体验,无需重新加载页面
- 减轻服务器负载,客户端处理部分逻辑
- 基于标准化的JavaScript,无需插件支持

AJAX对前后端分离和动态网站开发起到很大作用。但也需要注意跨域和安全问题。

