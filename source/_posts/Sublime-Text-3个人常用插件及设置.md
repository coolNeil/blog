---
title: Sublime Text 3个人常用插件及设置
date: 2017-04-07 16:49:20
categories:
  - Tools
tags:
  - Sublime Text
comments: false
---
## Package Control
```
import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
## Emmet
## Can I Use
## Gulp
## JavaScript Completions
## Java​Script & Node​JS Snippets
## Bracket Highlighter( Preferences -> package settings -> Bracket Highlighter -> Bracket Settings – User)
```json
{
  "bracket_styles": {
    "default": {
      "icon": "dot",
      // "color": "entity.name.class",
      "color": "brackethighlighter.default",
      "style": "highlight"
    },
    "unmatched": {
      "icon": "question",
      "color": "brackethighlighter.unmatched",
      "style": "highlight"
    },
    "curly": {
      "icon": "curly_bracket",
      "color": "brackethighlighter.curly",
      "style": "highlight"
    },
    "round": {
      "icon": "round_bracket",
      "color": "brackethighlighter.round",
      "style": "highlight"
    },
    "square": {
      "icon": "square_bracket",
      "color": "brackethighlighter.square",
      "style": "highlight"
    },
    "angle": {
      "icon": "angle_bracket",
      "color": "brackethighlighter.angle",
      "style": "highlight"
    },
    "tag": {
      "icon": "tag",
      "color": "brackethighlighter.tag",
      "style": "highlight"
    },
    "single_quote": {
      "icon": "single_quote",
      "color": "brackethighlighter.quote",
      "style": "highlight"
    },
    "double_quote": {
      "icon": "double_quote",
      "color": "brackethighlighter.quote",
      "style": "highlight"
    },
    "regex": {
      "icon": "regex",
      "color": "brackethighlighter.quote",
      "style": "outline"
    }
  }
}
```
## ConvertToUTF8
## AutoFileName
## AllAutocomplete
## DocBlockr
## AdvancedNewFile
## Trailing spaces
## SideBarEnhancements
```json
{ "keys": ["ctrl+shift+c"], "command": "copy_path" },
    //chrome
{
  "keys": ["f2"], "command": "side_bar_files_open_with",
  "args": 
  {
    "paths": [],
    "application": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe",
    "extensions":".*"
  }
}
```
## Terminal
```json
{
  // window下终端路径
  "terminal": "C:/#Alan/software/cmder/Cmder.exe",
  // window下终端参数
  "parameters": ["/START", "%CWD%"]
}
```
## Themr
## Seti_UI
## Material Theme-Appbar
## Material Theme
## Colorsublime：Candy Crush
## MarkDownPreview
```json
{
  "keys": ["alt+m"],
  "command": "markdown_preview",
  "args": { "target": "browser"}
}
```
## MarkDownEditing
## Sublimeserver
## ColorHighlighter
```json
{
  "ha_style": "filled",
  "icons": false
}
```
## HTML-CSS-JS Prettify
## Babel
## Jsformat
```json
{
  // 在包中设置
  // 为了支持jsx
  "e4x": true,
  // jsformat options
  "format_on_save": true,
}
```
## React Es6 Snippets
```json
{ "keys": ["tab"], "command": "expand_abbreviation_by_tab",
  "context": [
    {
      "operand": "source.js", 
      "operator": "equal", 
      "match_all": true, 
      "key": "selector"
    },
    {   
      "key": "selection_empty", 
      "operator": "equal", 
      "operand": true,
      "match_all": true 
    }
  ]
},
{ "keys": ["tab"], "command": "next_field", "context":
  [
    { "key": "has_next_field", "operator": "equal", "operand": true }
  ]
}
```
## 常用快捷键
```js
"Alt + F3"  // 快速全选
"Ctrl + R" // 快速选择函数和css中的选择器
"Ctrl + G" // 选择行号
"Ctrl + :" // 查找变量名、属性名
"Shift + 鼠标右键拖动" // 快速添加游标
"Shift + 上下左右" // 选择文字
"Ctrl + L" // 选择一整行
"Ctrl + KK" // 从光标处开始删除代码至结尾
"Ctrl + Shift + " " // 只选择标签，但是属性不变
"Ctrl + Shift + ;" // 移除标签
"Ctrl + j" // 合并为一行
"Ctrl + Shift + j" // 选择父容器中的内容
"Ctrl + k" // 跳过同名单词
"Ctrl + M" //  在起始括号和结尾括号之间跳转
"Ctrl + Shift + M" // 选择{}中所有的内容，使用于css与js

"Alt + Shift + W" // 标签包裹

"Ctrl+Tab" // 当前窗口中的标签页切换
"Alt+Shift+2" // 左右分屏-2列
"Ctrl+Shift+分屏序号" // 将当前焦点页分配到分屏序号页

"Ctrl+K+T" // 折叠属性
"Ctrl+K+0" // 展开所有

"F6" // 单词拼写检查
```
## 设置
```json
{
	"bold_folder_labels": true,
	"caret_style": "phase",
	"color_scheme": "Packages/Babel/Monokai Phoenix.tmTheme",
	"font_size": 12,
	"highlight_line": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"line_padding_bottom": 1,
	"line_padding_top": 1,
	"rulers":
	[
		80,
		100
	],
	"tab_size": 2,
	"theme": "Seti.sublime-theme",
	"translate_tabs_to_spaces": true,
	"trim_trailing_white_space_on_save": true,
	"word_wrap": true
}
```
## 快捷键设置
```json
[
  {
    "keys": [
      "ctrl+shift+c"
    ],
    "command": "copy_path"
  },
  {
    "keys": [
      "f2"
    ],
    "command": "side_bar_files_open_with",
    "args": {
      "paths": [],
      "application": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe",
      "extensions": ".*"
    }
  },
  {
    "keys": [
      "alt+m"
    ],
    "command": "markdown_preview",
    "args": {
      "target": "browser"
    }
  },
  {
    "keys": [
      "tab"
    ],
    "command": "expand_abbreviation_by_tab",
    "context": [
      {
        "operand": "source.js",
        "operator": "equal",
        "match_all": true,
        "key": "selector"
      },
      {
        "key": "selection_empty",
        "operator": "equal",
        "operand": true,
        "match_all": true
      }
    ]
  },
  {
    "keys": [
      "tab"
    ],
    "command": "next_field",
    "context": [
      {
        "key": "has_next_field",
        "operator": "equal",
        "operand": true
      }
    ]
  }
]
```