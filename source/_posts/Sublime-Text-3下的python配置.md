---
title: Sublime Text 3下的python配置
date: 2017-04-12 16:03:00
categories:
  - Python
tags:
  - Python
  - Sublime Text
---

# Python的安装
  * 下载安装python
  * 配置python到系统环境变量中的path属性中去

# Build System
  * Tool—>Build System->New Build System
  * 添加如下代码并保存为Python.sublime-build
  ```json
  {
    "cmd": ["C:\\Users\\Alan_\\AppData\\Local\\Programs\\Python\\Python36-32\\python.exe","-u","$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python"
  }
  ```
  * 新建一个python文件，ctrl+b就可以出效果了

