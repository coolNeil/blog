---
title: interview
date: 2017-04-14 11:19:56
categories:
  - 其他
tags:
  - 面试
comments: false
---

# js自定义log方法

```js
function log() {
    console.log.apply(console, arguments);
}
```

console.log.apply(console, arguments)的意思是:
让上面声明的那个log中的this由原来的指向切换到新的指向，让它指向console对象，因为console内部机制，用window调用是不合法的，只能用console自己调用！
第二个参数的目的是为了达到可以一次接受一个参数arguments列表。
理解误区：
console.log.apply(console, arguments)等同console.log(arguments)而不是console(arguments)，且此时的console.log是被apply处理过的，可以一次接受若干参数。