---
title: web.xml常用配置
date: 2019-12-09 18:21:04
tags:
---
1. 修改web应用默认首页
``` xml
 <welcome-file-list>

        <welcome-file>index.html</welcome-file>
        <welcome-file>default.html</welcome-file>
        <welcome-file>default.jsp</welcome-file>
    </welcome-file-list>
```
2. 使用servlet通配符映射及初始化参数
所有对http://localhost:8080/clcun/pattern/*的访问都会被patternServlet捕获
``` xml
 <servlet>
        <!-- seervlet的别名-->
        <servlet-name>patternServlet</servlet-name>
        <servlet-class>com.clcun.www.pattern.PatternServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>patternServlet</servlet-name>
        <url-pattern>/pattern/*</url-pattern>
    </servlet-mapping>
```
web.xml中初始化全局变量：
``` xml
<context-param>
        <param-name>title</param-name>
        <param-value>长岭村</param-value>
    </context-param>
```
获取这个变量：
```java
ServletContext context = request.getServletContext();
String title = (String) context.getAttribute("title");
```
3. 设置404,500等状态码默认页面
定义好错误页面404.html和500.html后，在web.xml中添加页面映射
```xml
<error-page>
     <error-code>404</error-code>
     <location>/error/404.html</location>
 </error-page>
    <error-page>
        <error-code>500</error-code>
        <location>/error/500.html</location>
    </error-page>
```