# 在 JavaScript 中如何浅复制一个对象

## 参考答案

使用对象扩展运算符 `...`，可以复制对象自己的可枚举属性到新的对象。完成对象的浅层克隆。

```es6
const obj = { a: 1, b: 2 }
const shallowClone = { ...obj }
```

使用这种技术时，prototypes将会被忽略。此外，不会克隆嵌套对象，而是复制它们的引用，因此嵌套对象仍然引用原始的对象。深度克隆要复杂得多，因为要有效地克隆可能嵌套在对象中的任何类型的对象（Date，RegExp，Function，Set等）。

其他方法有:

* `JSON.parse(JSON.stringify(obj))` 可用于深度克隆一个简单的对象，但它是CPU密集型的，且只接受有效的JSON。
* `Object.assign({}, obj)` 大体上等同于 {{}, ...obj}.
* `Object.keys(obj).reduce((acc, key) => (acc[key] = obj[key], acc), {})` 是另一个更冗长的替代方案，更深入地展示了这个概念。

## 关键点

* JavaScript通过引用传递对象，这意味着嵌套对象将复制它们的引用，而不是它们的值。
* 可以使用相同的方法合并两个对象。

## 额外参考

<!-- tags: (javascript) -->
