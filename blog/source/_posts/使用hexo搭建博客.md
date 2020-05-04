---
title: 使用hexo搭建博客
date: 2019-11-20 23:54:02
tags:
---

## 1. 环境安装
### 1.1 Node.js安装

## 2. 命令操作
### 2.1 hexo命令

### 2.2 用到的Linux命令
#### 2.2.1 发布博客时，将生成的网站静态页面，复制到github目录下，  

```
cp -r -force public\* .\.deploy\username.github.io
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
