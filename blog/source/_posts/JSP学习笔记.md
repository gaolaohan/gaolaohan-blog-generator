---
title: JSP学习笔记
date: 2019-12-04 23:38:36
tags:
---
jsp本质就是Servlet，tomcat接收到请求，找到jsp先转为Servlet.java 然后编译。
JSP语法：
1. JSP代码块 在JSP中嵌入Java代码 <% java代码 %>
2. JSP声明构造块 <%! 声明语句%> <%! public int add(int a, int b){return a+b} %>
3. JSP输出指令 显示java代码执行的结果 <%= 表达式或者变量%> 等于 <% out.println%>
4. JSP处理指令 jsp提供辅助信息 <%@ jsp指令%> 例如 <%@ page import="java.util.*" %>
   <%@ page %> 定义当前jsp页面全局设置
   <%@ include %> 将其他jsp页面与当前JSP页面合并
   <%@ taglib %> 引入JSP标签库
JSP注释：
<%-- --%> JSP 注释
// /*..*/ 注释java代码
<!-- html --> html注释，被注释的语句不会被浏览器解析

