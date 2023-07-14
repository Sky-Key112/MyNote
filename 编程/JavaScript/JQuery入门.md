# JQuery

## 入口
```js
  $(document).ready(function() {
    // 页面加载完成后执行
  });
```

## 语法
jQuery的基本语法如下:

1. 选择元素

使用CSS选择器来选取元素,并返回jQuery对象:

```js
$('selector') 
```

例如:$('#id')、$('.class')

2. 操作元素

调用jQuery对象的方法来操作元素:

```js
$('selector').action()
```

例如:.text()、.html()、.css() 

3. 事件绑定

在jQuery对象上绑定事件响应函数:

```js 
$('selector').event(function(){})


例如:.click(function(){})、.mouseover(function(){})
```
4. 链式调用

jQuery方法可以链式调用:

```js
$('selector').action1().action2().action3();
```

5. 传入回调函数

某些方法会传入回调函数,在动画或ajax完成后执行:

```js
$('selector').animate({}, function(){
  // 动画完成回调
})
```
