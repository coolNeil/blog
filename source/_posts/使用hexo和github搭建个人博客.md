---
title: 使用hexo和github搭建个人博客
date: 2017-04-07 15:15:39
categories:
  - Tools
tags:
  - hexo
comments: false
---

### 环境搭建
  - Node.js
  - git
  - github账号

### hexo
  * 安装
    - `npm install hexo -g`
  * 初始化
    - `hexo init`
  * 生成静态页
    - `hexo generate | hexo g`
  * 本地启动
    - `hexo server`
  * 新建博客文章 `hexo new [layout] "postName"`
    1. 博文会自动生成在博客目录下source/_posts/postName.md
    2. 如果layout没有传入, 会使用_config.yml文件中的default_layout字段,默认是post
  * 生成静态页 `hexo g`

### 部署到github
  - github上建一个仓库，名字必须是your_user_name.github.io
  - `sh-keygen -t rsa -C "your_email@example.com`生成公钥密钥
  - 将公钥放到github
    * 验证是否通过 `ssh -T git@github.com`
  - 配置hexo关联到github（repo属性的值是你自己的仓库地址）
    ```
    deploy:
    type: git

    repo: git@github.com:coolNeil/coolNeil.github.io.git

    branch: master
    ```
  - `npm install hexo-deployer-git --save`
  - 发布到github
    * `hexo deploy | hexo d`
    * 然后在浏览器输入`coolNeil.github.io`就能够查看了
  - 删除文章
    * `hexo clean`
    * 接着删除source/_posts/文件夹下面的文章
    * `hexo g`
    * `hexo d`

### 关联域名

### hexo主题（next）
  - 下载
    * `git clone https://github.com/iissnan/hexo-theme-next themes/next`
  - 启用
    * 在主配置文件中设置`theme: next`
    * 测试是否成功：`hexo s --debug`
  - next主题选择
    * 在主题配置文件中打开注释`scheme: Pisces`(此乃个人偏好)
  - 设置语言
    * 在主配置文件中：`language: zh-Hans`
  - 设置头像
    * 在主题配置文件中修改avatar属性
  - 设置作者昵称
    * 在主配置文件中修改author属性
  - 设置站点描述
    * 在主配置文件中修改description属性

### 部分问题
  - 分类页404解决(标签页类似)
    * `hexo new page "categories"`
    * 编辑新建的页面
      - 添加`type: "categories"`
      - 添加`comments: false`