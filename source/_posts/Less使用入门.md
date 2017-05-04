---
title: Less使用入门
date: 2017-05-04 18:21:40
categories:
  - CSS
tags:
  - Less
comments: false
---

# 变量

# 混合

* 不带参数
```less
.a, #b {
  color: red;
}
.mixin-class {
  .a(); // 也可以不加括号，写成.a
}
.mixin-id {
  #b();
}
```

* 带参数（可以有默认值）
```less
.rounded-corners (@radius: 5px) {
  -webkit-border-radius: @radius;
  -moz-border-radius: @radius;
  -ms-border-radius: @radius;
  -o-border-radius: @radius;
  border-radius: @radius;
}

#header {
  .rounded-corners;
}
#footer {
  .rounded-corners(10px);
}
```

# 匹配模式
（@_表示不论.mixin匹配到那种情况，都会被编译进去）
```less
.mixin(dark; @color) {
  color: darken(@color, 10%);
}
.mixin(light; @color) {
  color: lighten(@color, 10%);
}
.mixin(@_; @color) {
  display: block;
}
```

# 嵌套
```less
#header {
  h1 {
      font-size: 26px;
      font-weight: bold;
  }
  p {
      font-size: 12px;
      a {
          text-decoration: none;
          &:hover {
              border-width: 1px
          }
      }
  }
}
```

# 避免编译
~''

参考资料：
1. [Less中文](http://www.1024i.com/demo/less/document.html)
2. [Less参考文档](http://www.css88.com/doc/less/features/#loops-feature)