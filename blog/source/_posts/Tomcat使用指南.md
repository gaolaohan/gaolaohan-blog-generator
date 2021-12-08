---
title: Tomcat使用指南
date: 2019-11-29 16:42:18
tags: "Tomcat"
categories: "编程"
---

tomcat放到服务器上访问8080端口还需要输入端口号，造成访问不便，好多人需要换成80端口。
改变端口号很简单，在tomcat/conf/server.xml里面改变port的值就可以。
```
<Connector URIEncoding="UTF-8" port="8080" protocol="HTTP/1.1"
connectionTimeout="20000"
redirectPort="8443" />
```
按理说就这样就可以，但是改成80后，用```service tomcat restart```,重启tomcat，
用```netstat -nlp```查看端口，发现没有80端口，
原来是在lunix下，非root用户不能监听1024以上的端口号，
这个tomcat服务器就没办法绑定在80端口下，
所以这里需要使用linux的端口转发机制，
把到80端口的服务请求都转到8080端口上。

iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
保存
service iptables save
这样就可以访问80端口了。

可以看到它的配置文件在/etc/tomcat8下，启动文件在/usr/share/tomcat8下
但是我们常见的webapps在哪里？其实它是在/var/lib/tomcat8下面，cd /var/lib/tomcat8后，我们可以看到熟悉的webapps文件夹。
cd 到/etc/tomcat8下可以看到tomcat全局配置文件。
Tomcat会自动对war包进行解压缩
Tomcat默认字符集是ISO-8859-9,西欧字符集

idea调试运行时，生成的工程文件存放在```C:\Users\gaota\.IntelliJIdea2019.2\system\tomcat\Tomcat_9_0_27_clcun```目录下

如果要在localhost后面取消输入上下文目录直接访问应用，在tomcat service.xml中做如下配置：
``` xml
<Context path="/" docBase="C:\coding\server\apache-tomcat-9.0.27\webapps\clcun" reloadable="true"/>
```
其中```path="/"```表示将应用的目录映射为应用服务器上的根目录