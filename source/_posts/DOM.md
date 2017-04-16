---
title: DOM
date: 2017-04-13 16:20:45
categories:
  - JavaScript
tags:
  - DOM
comments: false
---

## Node Properties:

* childNodes  空格/注释都会算节点，而children只会找到元素节点
* firstChild
* lastChild
* nextSibling
* nodeName
* nodeType
* nodeValue
* parentNode
* previousSibling

## Node Methods:

* appendChild()
* cloneNode()
* compareDocumentPosition()
* contains()
* hasChildNodes()
* insertBefore() parentElement.insertBefore(newElement, targetElement) //targetElement是指在newElement之后的元素
* isEqualNode()
* removeChild()
* replaceChild()

## Document Methods:

* document.createElement()
* document.createTextNode()

## HTML * Element Properties:

* innerHTML
* outerHTML
* textContent
* innerText
* outerText
* firstElementChild
* lastElementChild
* nextElementChild
* previousElementChild
* children

## HTML element Methods:

* insertAdjacentHTML()

## Node Properties

* createElement()
* tagName
* children
* getAttribute()
* setAttribute()
* hasAttribute()
* removeAttribute()
* classList()
* dataset
* attributes

## 长度

* offsetLeft
* offsetTop
* offsetParent

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <style>
    body {
        margin: 0;
    }

    #blue {
        height: 100px;
        width: 100px;
        background-color: blue;
        border: 10px solid gray;
        padding: 25px;
        margin: 25px;
    }

    #red {
        height: 50px;
        width: 50px;
        background-color: red;
        border: 10px solid gray;
    }
    </style>
</head>

<body>
    <div id="blue">
        <div id="red"></div>
    </div>
    <script>
    var div = document.querySelector('#red');

    console.log(div.offsetLeft); //logs 60
    console.log(div.offsetTop); //logs 60
    console.log(div.offsetParent); //logs <body>
    </script>
</body>

</html>
```

![](/images/offsetTop-offsetLeft.png)

- getBoundingClientRect()  得到的是一个对象，里面保存了top/bottom/left/right/height/width
  + top/bottom都是以元素外边框相对于浏览器viewpoint的上边缘
  + left/bottom都是以元素外边框相对于浏览器viewpoint的左边缘
  + width/height = (border + padding + content)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <style>
    body {
        margin: 0;
    }

    div {
        height: 50px;
        width: 50px;
        background-color: red;
        border: 10px solid gray;
        margin: 100px;
    }
    </style>
</head>

<body>
    <div></div>
    <script>
    var divEdges = document.querySelector('div').getBoundingClientRect();

    console.log(divEdges.top, divEdges.right, divEdges.bottom, divEdges.left); //logs '100 170 170 100'
    </script>
</body>

</html>
```

![](/images/getBoudingClientRect.png)

* clientWidth and clientHeight = (padding + content) 不能包括滚动条
* scrollHeight and scrollWidth 获取的是被卷曲的元素的宽高，强调的是元素
* scrollTop and scrollLeft 获取上边和左边被卷曲的长度