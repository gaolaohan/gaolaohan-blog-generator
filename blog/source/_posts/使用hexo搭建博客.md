---
title: 使用hexo搭建博客
date: 2019-11-20 23:54:02
tags: "git"
categories: "工具"
---

## 1. 环境安装
### 1.1 Node.js安装

## 2. 命令操作
### 2.1 hexo命令
```
首先到 cd c:/hexo 下，
然后git pull git@github.com:gaolaohan/gaolaohan-blog-generator.git，
再到C:\coding\hexo\gaolaohan-blog-generator\下，hexo init blog，这时候会生成hexo框架的网站。
然后cd blog, 执行npm install
npm install=npm i。
在git clone项目的时候，项目文件中并没有 node_modules文件夹，项目的依赖文件可能很大。
直接执行，npm会根据package.json配置文件中的依赖配置下载安装。
hexo clean 清空网站项目
hexo g 生成网站
hexo s 打开本地web服务器，localhost:4000访问网站本地部署效果。
```

### 2.2 用到的Linux命令
#### 2.2.1 发布博客时，将生成的网站静态页面，复制到github目录下，  

```
cp -r -force public\* .\.deploy\username.github.io
复制到该目录下后，进入username.github.io 目录，执行：
git add .
git commit -m "备注"
git push 发布到github上，网站内容同步就更新了。
```

```
Git报错解决：OpenSSL SSL_read: Connection was reset
首先，造成这个错误很有可能是网络不稳定，连接超时导致的，
如果再次尝试后依然报错，可以执行下面的命令。
打开Git命令页面，执行git命令脚本：修改设置，解除ssl验证
git config --global http.sslVerify "false"
```

## 3. 常见问题
### 3.1 next主题
#### 3.1.2 设置首页不显示全文
next主题的首页默认会把每一篇文章的全部内容展示出来，非常不美观。如果想设为只预览一部分，修改主题下_config.yml文件中auto_excerpt: enable: true 即可。
#### 3.1.2 主题修改语言
到Hexo站点根目录\themes\next\languages文件夹下看有支持哪些语言，中文有以下三种，  

- zh-CN.yml
- zh-HK.yml
- zh-TW.yml

打开站点根目录/_config.yml文件，设置language内容为： ```language: zh-CN``` 

### 3.2 将网站生成代码备份到github
