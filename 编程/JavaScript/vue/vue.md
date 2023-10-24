

在使用 Vue.js 构造 Vue 实例时,最常用和重要的实例选项主要有:

- el - 描定 Vue 实例挂载的 DOM 元素,可以是 CSS 选择器,也可以是 DOM 对象

- data - Vue 实例的数据对象,用于定义属性

- methods - Vue 实例的方法,会被绑定到实例上

- computed - 计算属性,对于复杂的计算结果进行缓存

- watch - 监听数据变化的回调函数

- components - 局部注册的组件

- props - 定义组件可接收的 props

- directives - 局部注册的指令

- filters - 过滤器,用于文本格式化输出

- mixins - 混入,组件间代码复用

- template - 模板字符串替代外部模板文件

- render - 代替 template 使用 JS 渲染函数

- mounted - 组件挂载完毕的回调钩子

- created - 实例创建完毕的回调钩子 

等等

这些选项覆盖了一个 Vue 组件从初始化到渲染的大部分功能,是非常常用和重要的。

特别是 template、data、methods、computed 是构建组件必备的选项,el 和 mounted 用于控制组件的挂载。

可以根据需要使用其它补充选项,构成一个功能完整的 Vue 组件。