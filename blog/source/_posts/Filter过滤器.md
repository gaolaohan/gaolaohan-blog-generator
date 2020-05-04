---
title: Filter过滤器
date: 2020-01-03 15:26:43
tags:
---
Filter从客户端浏览器向tomcat发来的请求进行统一拦截处理，也对响应进行处理，应用程序层面进行全局处理。

任何过滤器都必须实现Filter接口
doFilter()编写过滤器功能代码
在web.xml中对过滤器进行设置，说明拦截URL范围

Filter生命周期
tomat启动时，Filter对象会被创建，并立即执行Filter.init()方法，对当前过滤器进行初始化。
之后，每来一个请求，Filter.doFilter()提供服务，例如安全检查等；
tomcat重启或者关闭时，执行Filter.destroy()。
过滤器全局有且只有一个对象，启动时被创建。单例多线程来处理高并发请求，线程之间没有相互影响。
Filter配置形式
web.xml中配置
```xml
  <filter>
        <filter-name>firstfilter</filter-name>
        <filter-class>com.clcun.filter.FirstFilter</filter-class>
    </filter>
<!--    url-pattern说明过滤器作用范围-->
    <filter-mapping>
        <filter-name>firstfilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```
Servlet3.0后可以使用注解，
```java
@WebFilter(filterNname="过滤器的名称",urlPatterns="/*")
public class MyFilter implements Filter{...}
```
tomcat如何知道类是过滤器呢？
Servlet3.0后tomcat会对class字节码文件进行扫描，如果类的上面有WebFilter就会认为是过滤器。
配置形式维护性更好，适合大型项目，适合全局过滤
注解形式开发体验更好，不需要在web.xml里面处理，适用于小型项目敏捷开发，但需要重新编译。

开发字符集过滤器


Get请求-在tomcat的server.xml增加URIEncoding="UTF-8"
Post请求-在request.setCharacterEncoding("utf-8");
响应：
response.setContentType("text/html;charset=utf-8")

J2EE 的servlet-api.jar定义了ServletRequest接口以及HttpServletRequest接口，但这只是接口，
接口的具体实现由第三方开发的类完成，比如HttpServletRequest接口在Tomcat中是由catalina.jar中的RequestFacade类实现。每一个客户端向服务器发来的请求数据，由ReuqestFacade进行解析。

过滤器参数化配置：
过滤器的设置项放在web.xml中。
<init-param>标签，在程序中动态提取。
```xml
      <filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>com.clcun.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
            <param-name>p1</param-name>
            <param-value>va1</param-value>
        </init-param>
    </filter>
```

   也可以通过注解方式
```java
    @WebFilter(filterName = "myAnnotationFilter", urlPatterns = "/*",
    initParams = {
        @WebInitParam(name="encoding", value="UTF-8"),
        @WebInitParam(name="p1", value = "v1")
    })
```
参数提取
```java
    private String encoding;
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        encoding= filterConfig.getInitParameter("encoding");
        System.out.println("encoding:" + encoding);
    }
```

UrlPattern设置过滤范围
1. /* 所有请求
2. /index.jsp 执行资源精准匹配
3. /servlet/* url中以servlet开头的url
4. *.jsp 以后缀名进行模糊匹配，所有jsp被匹配
5. 组合使用 /servlet/*.jsp 过滤以servlet开头以jsp结尾的url
过滤器中使用urlpattern /指映射web应用根目录，且只对servlet生效
/指向根目录，/*指向所有url
web.xml配置方式
```xml
    <filter>
        <filter-name>UrlPatternFilter</filter-name>
        <filter-class>
            com.clcun.filter.UrlPatternFilter
        </filter-class>
    </filter>
    <filter-mapping>
        <filter-name>UrlPatternFilter</filter-name>
        <url-pattern>/index.html</url-pattern>
    </filter-mapping>
    <filter-mapping>
        <filter-name>UrlPatternFilter</filter-name>
        <url-pattern>*.jsp</url-pattern>
    </filter-mapping>
```



注解形式

```java
@WebFilter(filterName = "UrlPatternFilters", urlPatterns = {
        "/", "/servlet/*", "*.jsp"
})
```
过滤器执行顺序由web.xml中的filter-mapping顺序决定
注意：下面的写法会报错，编译无法通过，应该是*.jsp没有/
```xml
<url-pattern>/*.jsp</url-pattern>
```
