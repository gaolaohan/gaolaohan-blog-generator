---
title: css定位
date: 2019-12-22 23:11:18
tags:
---
position:relatve 相对 absolute 绝对 static 无定位 fixed 固定
相对定位：偏移参考元素是元素本身不会使元素脱离文档流。元素的初始位置占据的空间会被保留。
偏移left或者top。相对的是自己以前的(0,0)位置，偏移(left,top)
相对定位一般用于包含其它子元素，配合其它子元素的显示效果。
绝对定位：参照物是最近的祖先元素，如果没有祖先元素就是以body作为参照物
position:absolute 脱离了文档流
```css
.main{
    top:20px;
    left: 20px;
    position: absolute;/*必须有position确定参照物,否则top和left不生效*/
    background-color: #123456;
    width: 500px;
    height: 500px;

}
```
固定定位：相对于浏览器窗口进行定位，就是滚动条变化也不会改变显示位置。
position:fixed
