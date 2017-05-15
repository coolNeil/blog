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

# 排序算法
[各个算法动画演示](http://math.hws.edu/eck/jsdemo/sortlab.html)

* 冒泡排序

```js
function bubbleSort(arr) {
  var len = arr.length;
  // 外层循环只负责比较的趟数
  for (var i = 0; i < len; i++) {
    // 内层循环负责比较相邻的两个数，最后比较arr[0]和arr[1],注意j的临界条件
    for (var j = 0; j < len - 1 - i; j++) {
      // 相邻元素两两比较，将大的往后挪
      if (arr[j] > arr[j + 1]) {
        var temp = arr[j + 1];
        arr[j + 1] = arr[j];
        arr[j] = temp;
      }
    }
  }
  return arr;
}

function bubbleSort(arr) {
  var numElements = arr.length;
  // outer表示外层剩余的未比较的个数，最少剩两个，剩两个的时候，直接比较内部的就可以了
  for (var outer = numElements; outer >= 2; --outer) {
    // 内层表示从头开始比较相邻两个数，注意inner只会比较到outer的倒数第二项
    for (var inner = 0; inner < outer - 1; ++inner) {

      if (arr[inner] > arr[inner + 1]) {
        var temp = arr[inner + 1];
        arr[inner + 1] = arr[inner];
        arr[inner] = temp;
      }
    }
  }
  return arr;
}
```

* 选择排序

```js
function selectionSort(arr) {
  var len = arr.length;
  var minIndex,
      temp;
  // 外层循环控制最小index开始位置，默认从第一项开始，一直到数组的倒数第二项为止
  for (var i = 0; i < len - 1; i++) {
    minIndex = i;
    // 内层循环将剩下的所有的数与最小数比较，如果比最小数小，那么就将该数索引赋值给最小index
    for (var j = i + 1; j < len; j++) {
      if (arr[j] < arr[minIndex]) { //寻找最小的数
        minIndex = j; //将最小数的索引保存
      }
    }
    // 获取到最小值索引之后，将该索引数值放置到最小index的位置
    temp = arr[i];
    arr[i] = arr[minIndex];
    arr[minIndex] = temp;
  }
  return arr;
}
```

* 插入排序

```js
function insertionSort(arr) {
  var temp,
      inner;
  // 从下标为1(也就是第二个)开始一直到最后，outer表示把拿出来放进temp的索引
  for (var outer = 1; outer < arr.length; ++outer) {
    // 先把第二个拿出来放进temp中
    temp = arr[outer];
    // inner指向的始终是那个空挡
    inner = outer;
    // 当拿出来放进temp中的前一项比temp大或等的时候
    while (inner > 0 && (arr[inner - 1] >= temp)) {
      // 就将那一项往后移
      arr[inner] = arr[inner - 1];
      --inner;
    }
    // 如果不是比temp大或等，直接将temp插入到inner位置就行
    arr[inner] = temp;
  }
  return arr;
}
```

# 数组去重

```js
function sort(arr) {
  var obj = {};
  var temp = [];
  for (var i = 0; i < arr.length; i++) {
    // 判断这个对象的属性是否和数组的值相同，相同则不添加，否则给这个对象添加这个值
    if (!(obj[arr[i]] === arr[i])) {
      obj[arr[i]] = arr[i];
      // 把这个过滤完以后的值添加到我们的新数组中。
      temp.push(arr[i]);
    }
  }
  return temp;
}
```


