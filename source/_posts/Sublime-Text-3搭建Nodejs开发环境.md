---
title: Sublime Text 3搭建Node.js开发环境
date: 2017-04-14 00:31:28
categories:
  - Node.js
tags:
  - Sublime Text
  - Node.js
comments: false
---

# Nodejs.sublime-build的创建
```json
{
  "cmd": ["node", "$file"],
  "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
  "selector": "source.js",
  "shell":true,
  "encoding": "utf8",
  "windows":
    {
        "cmd": ["taskkill","/F", "/IM", "node.exe","&","node", "$file"]
    },
  "linux":
    {
        "cmd": ["killall node; node", "$file"]
    }
}
```

# Nodejs插件的设置
```json
{
  // save before running commands
  "save_first": true,
  // if present, use this command instead of plain "node"
  // e.g. "/usr/bin/node" or "C:\bin\node.exe"
  "node_command": "C:\\dev\\nodejs\\node.exe", //node.exe 的位置
  // Same for NPM command
  "npm_command": "C:\\dev\\nvm\\npm\\npm.cmd", //npm.cmd 的位置
  // as 'NODE_PATH' environment variable for node runtime
  "node_path":true,

  "expert_mode": false,

  "ouput_to_new_tab": false,
}
```

# 验证是否配置成功(ctrl+b)
```js
var http = require('http');
var os = require('os');

http.createServer(function (request, response) {
  response.writeHead(200, {'Content-Type': 'text/plain'});
  response.end('Hello World\n');

}).listen(3000);

console.log('Server running at http://127.0.0.1:3000/');
```
