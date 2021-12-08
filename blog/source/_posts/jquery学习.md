---
title: jquery学习
date: 2019-12-16 18:34:33
tags: "javascript"
categories: "编程"
---
属性选择器：
$("a[href='http://www.clcun.com']") 选择属性值为clcun的超链接
$("a[href^='http://mail.']") 选择属性值前缀为http://mail.的超链接
$("a[href$='edu.cn']") 选择属性值结尾为edu.cn的超链接
$("a[href*='edu.cn']") 选择属性值包含edu.cn的超链接

$("ul li") 后代选择器
$(ul>li")子选择器
$("ul~li") 兄弟选择器

位置选择器
$("selector:first") 获取第一个元素
$("selector:last") 获取最后一个元素
$("selector:even") 偶数位置元素
$("selector:odd") 奇数位置元素
$("selector:eq(n)") 第n个位置元素

表单选择器：获取表单元素的简化形式，如获取所有文本框
$("selector:input") 所有输入元素
$("selector:text") 获取文本框  
$("selector:password") 获取密码框
$("selector:submit") 获取提交按钮
$("selector:reset") 获取重置按钮

操作元素的属性
attr(name|properties|key) 获取或设置元素属性
removeAttr(name) 移除元素属性
```javascript
var href_attr = jQuery("a[href*='163']").attr("href");//获取属性
alert(href_attr);
jQuery("a[href*='163']").attr("href", "http://www.clcun.com");
$("a").removeAttr("href");
```

css()-获取或设置匹配元素的样式属性
addClass()-为匹配的元素添加指定的类名
removeClass()-从所有匹配的元素中删除全部或者指定的类
```javascript
$("a").css("color", "red");
$("a").css({"color": "red","font-weight":"bold", "font-style":"italic"});
var coloar = $("a").css("color");
```

```javascript
$("li").addClass("highlight myclass");//添加若干个类
$("li").removeClass("highlight myclass");
```

设置元素的内容
val()-获取或者设置输入项的值
text()-获取或者设置元素的纯文本
html()-获取或者设置元素内部html
text对于文本中的html标签不进行转义，直接输出；html方法会进行转义。
```javascript
$("input[name='uname']").val("administrator");
var inputstr = $("input[name='uname']").val();
//alert(inputstr);
$("span.myclass").text("<b>锄禾日当午</b>");
$("span.myclass").html("<b>锄禾日当午</b>");
var varspan = $("span.myclass").text();
```

jquery事件
on("click", function)-为选中的页面元素绑定单击事件
clcik(function)-单击事件的简化写法
处理方法中提供了event参数，包含了事件的相关信息
鼠标事件：click dbclick mouseenter mouseleave mouseover
键盘事件：keypress keydown keyup
表单事件：submit change focus blur
文档窗口事件：load resize scroll 窗口滚动 unload 窗口关闭

```javascript
$("p.myclass").on("click", function () {
//当前事件对应的对象
$(this).css("background-color", "yellow");
});

$("span.myclass").click(function () {
$(this).css("background-color", "green");
});
```
event事件的处理：输入空格时提示错误，将文本设置为红色
```javascript
  $("input[name='uname']").keypress(function (event) {
        console.log(event);//查看事件的具体细节
        if (event.keyCode = 32) {
            $(this).css("color", "red");
        }
    });
```

