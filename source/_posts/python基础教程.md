---
title: python基础教程
date: 2017-04-12 16:36:24
categories:
  - Python
tags:
  - Python
comments: false
---

# Tips
* Clear Screen
```python
imoprt os
clear = lambda: os.system('cls')
clear()
```
* Keywords
```python
import keyword
keyword.kwlist
```


# First Program in Python
```python
print("welcome")
```

# Data Types
```python
type(2)
type(2.2)
type(2000000)
type(True)
type('a')
```

# Variables
```python
number = 2
real = 2.2
word = "word"
pint(word)
type(word)

a = b = c = 1.5
print(a)
print(b)
print(c)

one, two, three = 1, 'two', 'three'
print(one)
print(two)
print(three)

number = 1
str = 'string'
number = str
```

# Comments
* Single-line
```python
# 单行注释
```
* Multi-line
```python
'''
多行注释
'''
```

# Expression in Python
```python
print(2.0+5)
print(10.0-5)
print(40*3*0.5)
print(2**3) # 乘方
```

# String
```python
string = '012345'
print(string[2:5])
print(string[:5])
print(string[3])

string2 = ('con' + 'sole') * 2
print(string2)

i = "I"
can = "can"
print(i + can);

word = "Ford"
word = "L" + word[1:]
print(word)
word([2]) = "f"  # 会报错，字符串不允许修改

# 这种写法表示内部的字符不转义
print(r'c:\number\nan')

# 如果这里没有\会多一个空行
print('''\
  hello:
    world
    world
  ''');

print("今天星期{0},天气{1}".format(3,"晴天"))
print('prices:({x}, {y}, {z})'.format(x = 2.0, y = 1.5, z = 5))
print("the {vehicle} had {0} crashes in {1} months".format(5,6,vehicle = 'car'))

print('{:<20}'.format("text"))
print('{:>20}'.format("text"))
print('{:b}'.format(21))  # 转二进制
print('{:x}'.format(21))  # 转八进制
print('{:o}'.format(21))  # 转十六进制
```

(未完待续)