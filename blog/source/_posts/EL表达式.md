---
title: EL表达式
date: 2019-12-09 20:19:47
tags:
---
EL（Expression Language）表达式语言，用于简化JSP的输出
格式：${表达式} 取代out
``` html
<h1>学生姓名：${student.name}</h1>
```

``` html
<h1>姓名：${requestScope.student.name}</h1>
<h1>评级：${requestScope.grade}</h1>
```

requestScope作用域对象。EL表达式内置四种作用域对象：

1. pageScope 从当前页面取值
2. requestScope 从当前请求中获取属性值
3. sessionScope 从当前会话中获取属性值
4. applicationScope 从当前应用中获取全局属性值 应用程序全局也就是ServletContext

书写时可以不写作用域对象，el将按上面四个作用域对象依次查找。

对于请求体或者URL中的参数：EL表达式内置param对象来简化参数的输出，语法${para.参数名}