---
title: ajax学习笔记
date: 2019-12-17 00:00:46
tags:
---
Asynchronous Javascript And XML (异步的javascript 和 XML)
对页面数据进行局部刷新
创建XMLHttpRequest对象
发送Ajax请求
服务器处理完成后返回响应，通过javascript对响应进行处理
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<input id="btnLoad" type="button" value="加载">
<div id="divContent"></div>
</body>
<script>
    document.getElementById("btnLoad").onclick = function () {
        //创建XMLHttpRequest对象
        var xmlhttp;
        if(window.XMLHttpRequest){
            xmlhttp = new XMLHttpRequest();
        }else {
            //IE5 IE6浏览器版本
            xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
        }
        console.log(xmlhttp);//查看xmlhttp的属性
        //发送Ajax请求
        xmlhttp.open("GET", "/jquery/ajax/content", true);//创建请求,true表示异步
          //同步的时候，send方法一直处于阻塞状态，必须等服务器返回信息后才往下执行
        xmlhttp.send();//发送请求

        //服务器处理完成后返回响应，通过javascript对响应进行处理
        //事件用于监听ajax的执行状态，1 请求未初始化，1服务器连接建立了，2请求已经被接收，3请求正在处理，4响应文本已经被接收
        //响应状态码xmlhttp.status200 成功，404 未扎到
         //如果选择了同步，onreadystatechange将失效
    //onreadystatechange专门给异步使用，只有当状态发生变化时，将调用onreadystatechange里面的函数
        xmlhttp.onreadystatechange = function () {
            if(xmlhttp.readyState==4&& xmlhttp.status == 200){
                var t= xmlhttp.responseText;
                alert(t);
                document.getElementById("divContent").innerHTML=t;
            }
        }
    };
</script>
</html>
```
jquery的$.ajax()方法使用：
1、传入的时一个json对象，用于描述发送的细节$.ajax(json);
2、常用的json对象设置：
url 发送请求地址；
type请求类型get/post;
data向服务器传递的参数
dataType服务器响应的数据类型text/json/xml/html/jsonp/script
success 接收响应时的处理函数
error 请求失败时的处理函数

