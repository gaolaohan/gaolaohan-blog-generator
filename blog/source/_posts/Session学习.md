---
title: Session学习
date: 2019-12-06 15:23:57
tags: "Java"
categories: "编程"
---
Cookie保存在客户端的信息可能会被前端用户更改，虽然加密了，但不可靠。
Session 用于保存与浏览器窗口对应的数据，信息存放在服务器上。
Session数据存放在Tomcat服务器内存中，具有时效性，和前端浏览器窗口绑定；
如果没有人访问，有效时长保存30分钟。就是说一个浏览器窗口在tomcat服务器上有一个时效性30分钟的存储区域。
Session通过浏览器Cookie的SessionId值提取用户数据。

Session设置属性
``` java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("用户登陆成功");
        //获取到用户会话Session对象
        HttpSession session = request.getSession();
        String sessionId = session.getId();
        System.out.println("login" +sessionId);
        //设置属性
        session.setAttribute("username", "高涛");
        request.getRequestDispatcher("/session/index").forward(request, response);

    }
```
Session提取属性
``` java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        HttpSession session = request.getSession();
        String userName = (String) session.getAttribute("username");
        String sessionId = session.getId();
        System.out.println("index" +sessionId);
        response.setContentType("text/html;charset=utf-8");
        response.getWriter().println("这是首页，当前登录用户：" + userName);
    }
```

