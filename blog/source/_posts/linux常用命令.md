---
title: linux常用命令
date: 2019-11-21 20:55:05
tags:
---

## 1. 文件操作
### 1.1 删除文件或目录



命令 选项 参数1 参数2
ls -l (以长格式) /
shutdown -h now 
重启 shutdown -r now === reboot

linux 目录 根目录 /
/bin  存放命令的目录  普通用户和超级root用户
 /sbin 存放命令的目录 只有root用户可以使用
 /boot 启动目录
 /dev 设备文件存放的目录 例如硬盘
 /etc 配置文件
 /lib 函数库
 /home 普通用户目录
 /mnt U盘等挂载的
 /media 媒体设备挂在目录
 /opt 第三方软件安装目录
 /root 
 /tmp 临时文件存放
 /proc 存放的文件直接加载到内存中
 /srv 服务存放数据的目录
 /usr 系统软件存放的目录
 /var 软件相关的文档目录

 ls -l  /etc 以长格式输出 显示文件权限 所有组 归谁管理 大小
 ls -al /etc 显示隐藏的文件
 ls -a 显示所有文件 包含隐藏文件
 ls -alh h表示以我们方便的形式展示
 ls -alhS 文件按照大小顺序排列
 ls -alhSr 按照大小倒叙排列

ls --help 查看文件帮助
man ls 也可以查看ls 的帮助
 pwd 查看当前命令
 cd ..
 cd ~ 到家目录
 mkdir a 创建目录
mkdir /root/b
mkdir -p c/d 依次创建目录

rmdir a 删除目录
rmdir -p c/d/e 依次删除所有目录


文件查看 

cat -n a.txt 显示行号
more a.txt 一页一页显示 按空格一页显示 回车 一行行显示
q退出
head 看前面几行 tail 显示最后几行


复制
cp （-r 循环复制目录） 来源文件（可以多个） 目标文件 
cp a.txt diraaa
cp a.txt b.txt diraaa 最后一个参数必须是文件夹
cp a.txt diraaa/c.txt 并且文件名字为c.txt 
cp -r bbb ccc 可以复制目录 -r循环复制bbb中内容
mv 来源文件 目标文件
rm -rf 文件或目录 删除

mv a.txt ddd  移动到新的目录
mv a.txt ddd/c.txt 移动同时修改名字
mv a.txt b.txt 当前目录下进行改名字
mv aaa ddd 可以移动目录

rm a.txt  输入y才可以删除
rm ./* 删除当前目录下所有文件
rm -r bbb 删除目录

查找
which 命令名  查找命令所在目录
特定目录查找 whereis 文件或目录 在几个特定目录查找

find 目录 [-name/user/size] 参数

find  ./ 当前目录下 -name 查找名称 1.txt 文件名
find / -name 1.txt 根目录下查找
find / -name 'passwd'  
find / -name 'pass*' *表示任意的个数的任意字符
find / -name 'pass??' ? 表示任意单个字符
find / -user 'root' 查找root用户创建的文件


用户管理：
查看当前连接的用户：who
 useradd [-g 群组] 用户名

 sudo useradd -g root gaoguqi 
 sudo passwd gaoguqi 给用户设置密码
 

 passwd 用户名
 userdel [-r] 用户名 -r 同时删除用户家目录


 groups [用户名]
 groupadd 群组名
 groupdel 名
 usermod -g 群组名 用户名 
群组管理：


r 读
w 写
x 执行
ls -l 
文件类型 所有者权限 所属组权限 其它用户权限
d rwx r-x r-x
- 表示文件
d 表示目录 
l 表示连接

chown -R 用户名 文件或目录 -R递归处理目录所有内容
chown -R 用户名:组名 文件或目录 -R递归处理目录所有内容
chgrp -R 组名 文件或目录 -R递归处理目录所有内容

修改权限
chmod - R xyz 文件或目录
x所有者权限 y 所属组权限 z 其它用户权限
r 4 w 2 x 1
7表示rwx
chmod -R 777 gaotao 
chmod -R 755 gaotao 

或者
chmod -R xyz 文件目录
x 角色 u  所属用户g 所有组o 其它用户 a全部 
y +- 增加或者取消
z r w x


gzip bizp2 xz tar 打包 zip 
tar [-ctxzjJvf] 压缩文件 [源文件]
c 打包压缩 t 查看内容 x 解打包解压缩
z 使用 gzip方式 j 使用bzip2 方式 J 使用xz 方式
v显示过程 f 指定压缩包名

tar -cvf mytar.tar 1.txt 

tar -cvf mytar.tar aaadir

使用gzip方式压缩打包
tar -czvf mytar.tar.gz 1.txt 

tar -czvf mytar.tar.gz aaadir

查看压缩包内容
tar -tvf mytar.tar

tar -tzvf mytar.tar.gz 

rm -rf *.txt 删除所有txt文件


curl wget 下载
tar 解压
编译前配置 ./configure 
make
make clean


下载rmp包
rmp -ivh 软件包
i安装 v显示详细信息 h 显示进度
rpm -q 安装包 查询是否安装
rmp -e 安装包 卸载

从yum源获取
yum list 名称 查询可以安装的软件包
yum -y install 软件包

yum remove  卸载
yum update 更新

apt-get install


ifconfig 查看ip地址
uname -a 显示Linux内核版本和系统
x86-64表示64位
cat /proc/version 查看linux 版本



## 2. 常用命令
### 2.1 文件操作


###2.2 vim 命令

```

创建文件 touch a.txt
vi 命令模式  
dd 剪切当前行
yy复制当前行
p 黏贴 光标下一行黏贴 shift p 光标上一行黏贴


a 光标后插入
A 当前行之后插入
i 光标前插入
I 当前行之前插入
o 当前行之下插入
O 上一行插入
编辑模式 

: 或/ 进入 行模式
w保存 
wq 保存并退出
q 退出
q! 不保存退出
:set nu 显示行号
clear 清除屏幕
```
### 2.3 进程管理
w 查看当前登录用户
ps -ef | grep pts 查看当前用户进程
kill -9 进程号 杀掉进程

## 3. 常见问题
### 3.1 远程连接客户端putty

``` markdown

--putty经常自动断开的问题
vim /etc/ssh/sshd_config
添加
ClientAliveInterval 30
ClientAliveCountMax 86400
这两行的意思分别是
1、服务端每隔多少秒向客户端发送一个心跳数据
2、客户端多少次没有相应，服务器自动断掉连接
然后重启service sshd restart

```
