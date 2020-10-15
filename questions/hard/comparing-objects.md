# 在 JavaScript 中如何判断两个对象相等

## 参考答案

尽管两个不同的对象使用相同的值具有相同的属性，但使用 `==` 或 `===` 进行比较时，可能会得不到你期望的结果。
这是因为比较操作是通过它们的引用（内存中的位置）进行比较，而不是比较的原始值。

为了测试两个对象在结构上是否相等，需要一个辅助函数。它会迭代每个对象的属性以测试它们是否具有相同的值，包括嵌套对象。
可选地，也可以通过传递 `true` 作为第三个参数来测试对象的原型的等效性。

```es6
function isDeepEqual(obj1, obj2, testPrototypes = false) {
  if (obj1 === obj2) {
    return true
  }

  if (typeof obj1 === "function" && typeof obj2 === "function") {
    return obj1.toString() === obj2.toString()
  }

  if (obj1 instanceof Date && obj2 instanceof Date) {
    return obj1.getTime() === obj2.getTime()
  }

  if (
    Object.prototype.toString.call(obj1) !==
      Object.prototype.toString.call(obj2) ||
    typeof obj1 !== "object"
  ) {
    return false
  }

  const prototypesAreEqual = testPrototypes
    ? isDeepEqual(
        Object.getPrototypeOf(obj1),
        Object.getPrototypeOf(obj2),
        true
      )
    : true

  const obj1Props = Object.getOwnPropertyNames(obj1)
  const obj2Props = Object.getOwnPropertyNames(obj2)

  return (
    obj1Props.length === obj2Props.length &&
    prototypesAreEqual &&
    obj1Props.every(prop => isDeepEqual(obj1[prop], obj2[prop]))
  )
}
```

## 关键点

* 字符串和数字等原语按其值进行比较;
* 对象通过它们的引用（内存中的位置）进行比较。

## 额外参考

<!-- tags: (javascript) -->
