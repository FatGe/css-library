# 什么是 stateless-components

## 参考答案

无状态组件是其行为不依赖于其状态的组件。无状态组件可以是 functional 组件或 class 组件。无状态功能组件更易于维护和测试，因为它们可以保证在相同的 prop 下产生相同的输出。当不需要使用生命周期钩子时，应首选无状态功能组件。

## 关键点

* 无状态组件与其状态无关;
* 无状态组件可以是 functional 或 class 组件;
* 无状态功能组件完全避免使用 `this` 关键字。

## 额外参考

* [React docs on State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

<!-- tags: (react,javascript) -->
