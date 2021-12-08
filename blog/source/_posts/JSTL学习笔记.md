---
title: JSTL学习笔记
date: 2019-12-12 13:37:39
tags: "Java"
categories: "编程"
---
JSTL JSP standard tag library JSP标准标签库
核心标签库-core
格式化输出标签库-fmt
sql操作标签库-sql
xml操作标签库-xml
函数标签库-functions
jsp页面中添加使用核心标签库
``` xml
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```
指定的是lib->中taglibs-standard-impl-1.2.5.jar/META-INF/c.tld的 ``` <uri>http://java.sun.com/jsp/jstl/core</uri>```
