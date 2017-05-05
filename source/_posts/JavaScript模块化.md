---
title: JavaScript模块化
date: 2017-05-03 15:07:28
categories:
  - JavaScript
tags:
  - 模块化
comments: false
---

# JavaScript模块原始写法

## 全局函数
 ```js
function m1() {　　　　
    //...
}　　
function m2() {　　　　
    //...
}
 ```
缺点：污染全局变量

## 对象写法
```js
var module1 = new Object({
    _count: 0,
    m1: function () {
        //...
    },
    m2: function () {
        //...
    }
});
```
缺点：会暴露所有模块成员，例如此处的_count是可以被修改的`module1._count = 4`

## IIFE
```js
var module1 = (function() {
    _count: 0,
    var m1 = function () {
        //...
    };
    var m2 = function () {
        //...
    };

    return {
        m1: m1,
        m2: m2
    };
})();
```

对上面的写法进行优化：

### 放大模式

给module1添加了m3功能

```js
var module1 = (function (mod){
　　mod.m3 = function () {
　　　　//...
　　};
　　return mod;
})(module1);
```

### 宽放大模式

避免可能出现的空对象

```js
var module1 = ( function (mod){
　　//...
　　return mod;
})(window.module1 || {});
```

### 引入全局变量
```js
var module1 = (function (mod, $) {
  //...
})(module1 || {}, jQuery);
```

# 使用规范写法

## AMD(Asynchronous Module Definition)
使用说明：[SeaJS](http://yslove.net/seajs/#use)

## CMD(Common Module Definition)
使用说明：[RequireJS](http://www.requirejs.cn/)

- AMD与CMD区别
    1. 模块定义时对以来的处理不同（实际上就是语法区别）
        + AMD推崇依赖前置，在定义模块的时候就要声明其依赖的模块
        + CMD推崇就近依赖，只有在用到某个模块的时候再去require
    2. 对**依赖模块**的执行时机处理不同
        + AMD在加载模块完成后就会执行改模块，所有模块都加载执行完后会进入require的回调函数，执行主逻辑，这样的效果就是依赖模块的执行顺序和书写顺序不一定一致，看网络速度，哪个先下载下来，哪个先执行，但是主逻辑一定在所有依赖加载完成后才执行
        + CMD加载完某个依赖模块后并不执行，只是下载而已（看到有require函数就去下载里面的模块），在所有依赖模块加载完成后进入主逻辑，遇到require语句的时候才执行对应的模块，这样模块的执行顺序和书写顺序是完全一致的


## CommonJS

+ 定义模块
根据CommonJS规范，一个单独的文件就是一个模块。每一个模块都是一个单独的作用域，也就是说，在该模块内部定义的变量，无法被其他模块读取，除非定义为global对象的属性

+ 导出模块
module.exports 或者 exports

+ 加载模块
require();

# ES6模块化写法


