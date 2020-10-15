# 为什么 React 的 HTML 中要使用 `className` 来代替 `class`

## 参考答案

React的理念一开始就是与浏览器 DOM API 一致而不是 HTML，因为它更接近地表示了元素的创建方式。在元素上设置`class`意味着使用`className` API：

```es6
const element = document.createElement("div")
element.className = "hello"
```

此外，在ES5之前，保留字不能用于对象：

```es6
const element = {
  attributes: {
    class: "hello"
  }
}
```

在 IE8 中，这将会引起错误。在现代环境中，如果尝试分配变量，解构将引发错误：

```es6
const { class } = this.props // Error
const { className } = this.props // All good
const { class: className } = this.props // All good, but cumbersome!
```

但是，`class` 可以毫无问题地用作 prop，如Preact等其他库中所见。React 目前允许你使用 `class`，但会抛出警告并将其转换为 `className`。目前有一个Open thread（截至2019年1月）讨论将 `className` 更改为 `class` 以减少混淆。

## 关键点

## 额外参考

<!-- tags: (react,javascript) -->
