
# async

async 是一个优秀的异步工具包，提供了很多异步处理的方法。

同时支持以下环境

1. nodejs 使用 async 包
2. 浏览器，浏览器使用 async-es 包


## 如果你的应用使用了 async包，IOS9抛出异常 Attempting to change value of a readonly property.

找到 async/internal/awaitify.js,注释掉以下代码

```js
Object.defineProperty(awaitable, 'name', {
    value: `awaitable(${asyncFn.name})`
})
```