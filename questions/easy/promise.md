# 什么是 Promise

## 参考答案

`Promise` 对象表示异步操作的最终完成（或失败）及其结果值。
例如以下这代码段，在100ms之后将结果字符串打印到标准输出。另外，请注意catch，它可用于错误处理。

```es6
new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("result")
  }, 100)
})
  .then(console.log)
  .catch(console.error)
```

## 关键点

## 额外参考

* [Master the JavaScript Interview: What is a Promise?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e772618)

<!-- tags: (javascript) -->
