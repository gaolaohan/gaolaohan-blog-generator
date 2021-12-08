---
title: git学习笔记
date: 2020-04-25 21:32:48
tags: "git"
categories: "工具"
---
## 1. git命令
### 1.1 git config --global user.name "gaolaohan"
### 1.2 git config --global user.email "gaotao@163.com"
### 1.3 ssh-keygen -t rsa -C "gaotao@163.com"
### 1.4 直接按回车，不需要设置密码，将会再C:\Users\gaota\.ssh 下生成id_rsa.pub公钥，将里面的内容复制，到github的SSH keys- new SSH Key 新增设定就好了。
### 1.5 测试是否配置成功ssh -T git@github.com，提示success即为配置成功。
### 1.6 git config --list 查看变量


