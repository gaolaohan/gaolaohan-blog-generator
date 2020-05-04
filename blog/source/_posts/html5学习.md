---
title: html5学习
date: 2020-03-13 23:08:27
tags:
---
图片属性
图片通常使用 alt 属性。 在图片不能显示时，它能替代图片显示。建议定义好图片的尺寸，在加载时可以预留指定空间，减少闪烁。比如：
``` html
<img src="syl.png" alt="HTML5" style="width:520px;height:1314px">
```
语义特性：HTML5 新标准中添加了拥有具体含义的 HTML 标签比如：```<article>、<footer>、<header>、<nav>、 <section> ```。

连通性：能够让你和服务器之间通过创新的新技术方法进行通信。

对本地离线存储的更好的支持。

用于媒介回放的 video 和 audio 元素。

用于绘画的 canvas 元素。

性能与集成特性：提供了非常显著的性能优化和更有效的计算机硬件使用。

设备兼容特性：能够处理各种输入和输出设备。

CSS3 特性。

section 标签 ```<section>```  表示文档中的一个区域（或节）。比如章节、页眉、页脚或文档中的其他部分，一般来说会包含一个标题。
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <section>
            <h1>section是什么？</h1>
            <p>一个新章节</p>
        </section>
    </body>
</html>
```
注：不要把```<section>``` 元素作为一个普通的 div 容器来使用。一般来说，一个 ```<section>``` 应该出现在文档大纲中。

article 标签
<article> 标签定义独立的内容。常常使用在论坛帖子，报纸文章，博客条目，用户评论等独立的内容项目之中。article 可以嵌套，内层的 article 对外层的 article 标签有隶属关系。

例子：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <article>
            <h1>实验楼是什么</h1>
            <p>一个在线学习的网站</p>
        </article>
    </body>
</html>
```
nav 标签```<nav>``` 标签定义导航链接的部分：描绘一个含有多个超链接的区域，这个区域包含转到其他页面，或者页面内部其他部分的链接列表。

例子：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <nav>
            <ul>
                <li><a href="#">HTML</a></li>
                <li><a href="#">CSS</a></li>
                <li><a href="#">JavaScript</a></li>
            </ul>
        </nav>
    </body>
</html>
```
注：并不是所有的链接都必须使用 ```<nav>``` 标签,它只用来将一些热门的链接放入导航栏。一个网页也可能含有多个 ```<nav>``` 标签,例如一个是网站内的导航列表,另一个是本页面内的导航列表。

header 标签 ```<header>``` 标签定义文档的页眉，通常是一些引导和导航信息。它不局限于写在网页头部，也可以写在网页内容里面。

通常 header 标签至少包含一个标题标记（h1-h6），还可以包括 hgroup 标签，还可以包括表格内容、标识、搜索表单、nav 导航等。
例子：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <header>
            <h1>网站标题</h1>
            <h1>网站副标题</h1>
        </header>
    </body>
</html>
```
footer 标签```<footer>``` 标签定义 section 或 document 的页脚，包含了与页面、文章或是部分内容有关的信息，比如说文章的作者或者日期。 它和 header 标签使用基本一样，可以在一个页面中多次使用，如果在一个区段的后面加入了 footer 标签，那么它就相当于该区段的页脚了。

例子：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <footer>
            <span>Copyright @2013-2019 实验楼在线教育</span>
        </footer>
    </body>
</html>
```
aside 标签```<aside>``` 标签表示一个和其余页面内容几乎无关的部分，被认为是独立于该内容的一部分并且可以被单独的拆分出来而不会使整体受影响。其通常表现为侧边栏或者嵌入内容。他们通常包含在工具条，例如来自词汇表的定义。也可能有其他类型的信息，例如相关的广告、笔者的传记、web 应用程序、个人资料信息，或在博客上的相关链接。

例子：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <aside>
            <h1>实验楼简介</h1>
            <p>一个在线学习的网站</p>
        </aside>
    </body>
</html>
```
figure 标签 ```<figure>``` 标签规定独立的流内容（图像、图表、照片、代码等等）。

figure 元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响。

例子：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>my page</title>
    </head>
    <body>
        <figure>
            <figcaption>figure 元素的标题</figcaption>
            <img src="img.gif" alt="figure标签" width="100px" height="100px" />
        </figure>
    </body>
</html>
```


###html5 视频
HTML5 规定了一种通过 video 元素来包含视频的标准方法。

视频格式和浏览器支持如下所示：

格式  浏览器
.ogg    FireFox 3.5+ ，chrome 5.0+ ，Opera 10.5+
.mp4/H.264  Safari 3.0+ ，chrome 5.0+ ，IE 9.0+
.webm   FireFox 4.0+ ，chrome 6.0+ ，Opera10.6+
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <video width="320" height="240" controls="controls">
            <source src="http://labfile.oss.aliyuncs.com/courses/1248/video.ogg" type="video/ogg">
            <source src="http://labfile.oss.aliyuncs.com/courses/1248/video.mp4" type="video/mp4">
            你的浏览器不支持video元素
        </video>
    </body>
</html>
```
注：```<video>``` 与 ```</video>``` 之间插入的内容是供不支持 video 元素的浏览器显示的。video 元素允许多个 source 元素，source 元素可以链接不同的视频文件，浏览器将使用第一个可识别的格式。上面的例子中是两个source源，但只会一个播放框。
引入单个文件也可以这样写：
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <video src="http://labfile.oss.aliyuncs.com/courses/1248/video.ogg" width="320" height="240" controls="controls">
            你的浏览器不支持video元素
        </video>
    </body>
</html>
```

字幕的简单使用
使用常用的 WebVtt 字幕格式，在 ```<video>``` 中使用 ```<track>```元素引入字幕。例如：
```html
 <track src="http://labfile.oss.aliyuncs.com/courses/1248/video_ch.vtt" srclang="zh"   kind="subtitles" label="中文" default>
<track src="http://labfile.oss.aliyuncs.com/courses/1248/video_en.vtt" srclang="en" kind="subtitles" label="English">

```
