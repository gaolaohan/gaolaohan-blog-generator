---
title: Servlet学习笔记
date: 2019-12-04 15:56:42
tags:
---
html form中的action属性就是表单提交以后发送的地址是什么，一般就是servlet的完整路径或者相对路径，http://localhost:8080 不需要填写。
接收用户参数，两个方法：
1、request.getParameter() 接收单个参数
2、request.getParameterValues() 接收多个同名参数

Servlet生命周期：
1、装载 - web.xml tomcat启动扫描web-inf中的web.xml文件，解析xml，绑定url
2、第一次访问web.xml中的url的时候，会对servlet进行创建，执行new Servlet对象
3、初始化servlet-init() 
4、提供service服务
5、重启或者关闭的时候servlet会执行destroy()进行销毁
tomcat全局中有且只有一个servlet对象

注解简化配置：
就不需要在web.xml中配置servlet信息了。
servlet核心注解：@WebServlet 
Tomcat启动时会扫描所有class文件，如果发现该类上面有WebServlet这个注解，会加载到url-类映射中。

启动Tomcat时加载Servlet
web.xml使用<load-on-startup>设置启动加载
<load-on-startup>0-9999</load-on-startup>
0优先级最高，9999最低。优先加载配置0的servlet
启动时加载在工作中常用于系统的预处理，费时费力的工作启动时先加载。

jsp本质就是Servlet，tomcat接收到请求，找到jsp先转为Servlet.java 然后编译。

ContentType决定浏览器采用何种方式对响应体进行处理
text/html html文档
text/plain 纯文本
image/jpeg 图片资源
text/xml xml文档

请求转发与页面重定向

Tomcat默认字符集是ISO-8859-9,西欧字符集
Servlet中请求与响应都要设置UTF-8字符集以支持中文。

对于post请求响应体处理，
``` java
request.setCharacterEncoding("utf-8");
```
对于get请求发送的中文，tomcat 8之后版本默认get请求发送中文就是utf-8格式，无需转换；
之前版本在文件C:\coding\server\apache-tomcat-9.0.27\conf\server.xml中修改为：
``` xml
Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" URIEncoding="UTF-8"/>
```
对于响应response的中文乱码处理：

``` java
        response.setContentType("text/html;charset=utf-8");
```