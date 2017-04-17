---
title: 通过nvm安装Nodejs
date: 2017-04-17 18:25:04
categories:
  - Nodejs
tags:
  - Nodejs
  - nvm
comments: false
---

# 安装NVM
+ 下载 nvm 包并安装到`C:\dev\nvm`目录下，下载 地址：`https://github.com/coreybutler/nvm-windows/releases`
+ 修改`C:\dev\nvm\settings.txt`为如下内容（我只添加了前两项）
`root: C:\dev\nvm 配置为nvm.exe的路径，根据你的实际情况修改`
`path: C:\dev\nodejs 配置为 node 快捷方式所在的目录，当我们用哪个版本的node时，就会将nvm文件夹下那个版本的node添加到这个path路径里`
`arch: 64 配置为当前操作系统的位数`
`proxy: none`
+ 添加环境变量：NVM_HOME的变量值为：C:\dev\nvm;NVM_SYMLINK的变量值为：C:\dev\nodejs;
+ 在path中添加以上两个变量:`;%NVM_HOME%;%NVM_SYMLINK%;`
+ 打开一个cmd窗口输入命令：nvm -v那么我们会看到当前nvm的版本信息。然后我们可以安装nodejs了。

# 安装Node
+ 继续输入命令：nvm install latest如果网络畅通，我们会看到正在下载的提示，下载完成后会让你use那个最新的node版本。
+ 如果你是第一次下载，在use之前，C:\dev目录下是没有nodejs这个文件夹的，在输入比如： nvm use 5.11.0 之后，你会发现，C:\dev目录下多了一个nodejs文件夹，这个文件夹不是单纯的文件夹，它是一个快捷方式，指向了 C:\dev\nvm 里的 v5.11.0 文件夹。
+ 同样的咱们可以下载其他版本的nodejs，这样通过命令:nvm use 版本号 比如：nvm use 5.11.0就可以轻松实现版本切换了。
+ 备注： 如果你的电脑系统是32 位的，那么在下载nodejs版本的时候，一定要指明 32 如： nvm install 5.11.0 32 这样在32位的电脑系统中，才可以使用，默认是64位的。

# 安装NPM
+ 通过以上方式，Node其实已经安装得差不多了，我们需要配置NPM的全局路径，以保证以后在不同Node版本下全局安装的包都在同一个路径下面
+ 首先我们进入命令模式，输入 npm config set prefix "C:\dev\nvm\npm" 回车，这是在配置npm的全局安装路径，然后在用户文件夹下会生成一个.npmrc的文件，用记事本打开后可以看到如下内容：`prefix=C:\dev\nvm\npm`
+ 然后继续在命令中输入： npm install npm -g 回车后会发现正在下载npm包，在C:\dev\nvm\npm目录中可以看到下载中的文件，以后我们只要用npm安装包的时候加上 -g 就可以把包安装在我们刚刚配置的全局路径下了。
+ 我们为这个npm配置环境变量： 变量名为：NPM_HOME，变量值为 ：C:\dev\nvm\npm
+ 在Path的最前面添加;%NPM_HOME%，注意了，这个一定要添加在%NVM_SYMLINK%之前，所以我们直接把它放到Path的最前面
+ 最后我们新打开一个命令窗口，输入npm -v,此时我们使用的就是我们统一下载的npm包了。

# 安装nrm
+ npm install nrm -g
+ nrm ls
+ nrm use xxx