---
title: Cookie学习
date: 2019-12-06 12:57:35
tags:
---
Cookie浏览器在本地保存文本内容：
登陆状态，用户资料等；Cookie具有时效性，内容会伴随请求发送给tomcat
C:\Users\gaota\AppData\Local\Google\Chrome\User Data\Default\Cookies
设置cookie的值和最大有效期
``` java
//        创建cookie需要两个参数，1、cookie名称2、要保存的数据
        Cookie cookie = new Cookie("user", "admin");
//        设置最大有效期，单位秒
        cookie.setMaxAge(60*60*24*7);
        response.addCookie(cookie);
```
获取cookie中的信息：
``` java
 protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        Cookie[] cs = request.getCookies();
        String user = null;
        if(cs==null)
        {

        }else {
            for (Cookie c : cs
            ) {
                System.out.println(c.getName() + ":" + c.getValue());
                if (c.getName().equals("user")) {
                    user = c.getValue();
                }
            }
        }
        response.setContentType("text/html;charset=utf-8");

        if(user==null)
        {
            response.getWriter().println("user not login");
        }else
        {
            response.getWriter().println( "当前用户：" + user);
        }
    }
```
