---
title: Windows PowerShell使用指南
date: 2019-11-21 20:59:05
tags:
---

## 1. 常见问题
### 1.1 提示无法执行脚本错误

powershell中不能执行脚本，提示‘because running scripts is disabled on this system’
原因：
powershell中默认的Execution policy 是restricted，使用Get-ExecutionPolicy查看

解决方法：
管理员权限打开powershell,设置Execution policy为Remotesigned

``` 
Set-ExecutionPolicy RemoteSigned
```
### 1.2 无法使用ssh命令
Github上下载OpenSSH解压后放到C:\Program Files目录下（其它目录也可以），然后把路径添加到环境变量-系统变量-Path中，重启powershell即可。


## 2. 常用命令
### 2.1 远程连接服务器
ssh -p 端口号 用户名@ip地址
