---
title: ServletContext学习
date: 2019-12-06 16:57:34
tags:
---
ServletContext(Servlet上下文对象),web应用全局对象；
整个web应用程序中有且只有一个ServletContext对象，随着web应用启动而创建，关闭或重启时销毁。
设置ServletContext属性
``` java
 protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        ServletContext context = request.getServletContext();
        context.setAttribute("copyright", "2019 clcun.com");
        context.setAttribute("title", "长岭村");
        response.getWriter().println("init success");
    }
```
获取ServletContext属性
```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        ServletContext context = request.getServletContext();
        String copyright = (String) context.getAttribute("copyright");
        String title = (String) context.getAttribute("title");
        response.setContentType("text/html;charset=utf-8");
        response.getWriter().println("<h1>" + title + "</h1>" + copyright);
    }
```