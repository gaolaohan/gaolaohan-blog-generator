---
title: Sublime下使用Markdown指南
date: 2019-11-21 13:54:02
tags: "Sublime"
categories: "工具"
---

## 1. Sublime插件
### 1.1 插件安装：
&emsp;&emsp;ctrl+shift+p调出命令面板，输入package control:install package 回车
### 1.2 常用插件：
#### 1.2.1 MarkdownEditing 　　
&emsp;&emsp;MarkdownEditing 插件用于在Sublime 中编辑md文件。在submlime 中默认是白色的，把`Preferences→ Package Settings → Markdown Editing → Markdown GFM Setting—Default` 复制到 `Preferences → Package Settings → Markdown Editing → Markdown GFM Setting—User`中，更改为如下代码，可以使用黑色主题：
```markdown
// "color_scheme": "Packages/MarkdownEditing/MarkdownEditor.tmTheme",
"color_scheme": "Packages/MarkdownEditing/MarkdownEditor-Dark.tmTheme",
```


#### 1.2.2 MarkdownPreview
&ensp;&ensp;&emsp;MarkdownPreview 插件用于在浏览器中预览md文件效果，使用预览功能有两种方式：  

1. 使用ctrl+shift+p 调出命令面板 输入mdp 选中preview in browser。  

2. 或者设置快捷键，在 `Preferences -> Key Bindings` 打开的文件的右侧栏的中括号中添加一行代码：  
`{ "keys": ["control+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"}  }`   
按 `control+m` 就可以直接在浏览器中预览了，也可设置为自己喜欢的按键。  
`parser: markdown` 也可设置为 `parser: github`，改为使用 Github 在线API 解析 markdown。

#### 1.2.3 MarkdownLivePreview 在编辑器中实时预览
&emsp;&emsp; MarkdownLivePreview 插件用于在编辑器中实时预览，方法有下面两种：

1. 使用快捷键 alt+m 
2. 或者 ctrl+shift+p 到命令面板，使用 `markdownlivepreview: edit current file`

## 2. Markdown语法

### 2.1 标题

使用#数量标识标题的级数。
代码：
```markdown
# 第一级标题
## 第二级标题
### 第三级标题
#### 第四级标题
##### 第五级标题
###### 第六级标题
```
效果：
# 第一级标题
## 第二级标题
### 第三级标题
#### 第四级标题
##### 第五级标题
###### 第六级标题

还有一种两级标题的实现方法，  
代码：

```markdown
第一级标题
===
第二级标题
---
```


效果:

第一阶标题
===
第二阶标题
---

### 2.2 倾斜加粗删除下划线
代码：
```markdown
*斜体* 或 _斜体_  
**粗体**  
***加粗斜体***  
~~删除线~~  
<u>下划线</u>  
```
*斜体* 或  _斜体_  
**粗体**  
***加粗斜体***  
~~删除线~~  
<u>下划线</u>  
下划线也可以通过html的span来实现。
代码：
```markdown
<span style="border-bottom:1px dashed green;">所添加的需要加下划线的行内文字</span>
```
效果：
<span style="border-bottom:1px dashed green;">所添加的需要加下划线的行内文字</span>

如果要在文字前后直接插入\*或\_，可以使用反斜线实现：



### 2.3 引用
使用标记符>对内容进行引用：  
代码：
```markdown
> 引用第一层
>> 引用第二层
>>> 第三层引用
> 重回第一层引用
```

效果：  

>  引用第一层
>> 引用第二层
>>> 第三层引用  
>
> 重回第一层引用

引用的区块内也可以使用其他的语法，包括标题、列表、代码区块等。  
代码：
```markdown
> 1.1 这是第一行列表项
>> 2.1 第二行列表项
>>> -第三行列表项
> ###代码引用示例
>  ```java
>  public string GetName(string id)
>  {
>     return("name");
>  }
>  ```
```

效果：
> 1.1 这是第一行列表项
>> 2.1 第二行列表项
>>> -第三行列表项
> ###代码引用示例
>  ```java
>  public string GetName(string id)
>  {
>     return("name");
>  }
>  ```

引用中内容如果需要换行，可以使用 `<br>` 。
代码：  

```markdown
> <u>悯农</u><br>
锄禾日当午，汗滴禾下土。<br>
谁知盘中餐，粒粒皆辛苦。
```

> <u>悯农</u><br>
锄禾日当午，汗滴禾下土。<br>
谁知盘中餐，粒粒皆辛苦。


### 2.4 插入代码
方式有两种：
利用 &apos;(~键)符号包裹代码
插入行内代码，即插入一个单词或者一句代码的情况，使用 &apos;code()&apos;这样的形式插入。  
多行代码 在代码段的前一行以及后一行使用三个反引号，比如:
```python
#!/usr/bin/env python3
print("hello");
```

或者使用缩进式插入多行代码，缩进式插入前方必须有空行；缩进使用四个空格或者一个制表符
一个代码区块会一直延续到没有缩进的那一行


    #include <stdio.h>
    int main(void)
    {

    }
代码区块中的内容，一般markdown语法不会被转换，这表示可以很容易地以Markdown语法撰写Markdown语法相关的文件。比如*便只是星号。  

```markdown
Markdown 目录：
[TOC]

Markdown 标题：
# 这是 H1
## 这是 H2
### 这是 H3

Markdown 列表：
- 列表项目
1. 列表项目

*斜体*或_斜体_
**粗体**
***加粗斜体***
~~删除线~~

Markdown 插入链接：
[链接文字](链接网址 "标题")

Markdown 插入图片：
![alt text](/path/to/img.jpg "Title")

Markdown 插入代码块：
​```python
#!/usr/bin/python3

print("Hello, World!");
​```

Markdown 引用：
> 引用内容

Markdown 分割线：
---

Markdown 换行：
<br>

Markdown 段首缩进：
&ensp; or &#8194; 表示一个半角的空格
&emsp; or &#8195;  表示一个全角的空格
&emsp;&emsp; 两个全角的空格（用的比较多）
&nbsp; or &#160; 不断行的空白格
```

### 2.5 插入链接
Markdown支持两种形式的链接语法。  

1. 行内形式：  
链接文字都是用 [方括号] 来标记，使用 (圆括号) 来把文字转成链接。还可以为链接文字配个Title， Title 属性是可选项。
代码：
```markdwon
格式：[显示文字](网址 "标题")
```
```markdown  
我在[北京邮电大学](www.bupt.edu.cn "北邮") 读书.
```
  效果：  
   我在[北京邮电大学](www.bupt.edu.cn "北邮") 读书.  
2. 参考形式：  
为参考形式的链接定一个[名称]方便在文章中多次引用。  
代码：
```markdown
[链接文字][name]
[name]:link "title"
```
```markdown
我在[北京邮电大学][1] 读书，女朋友在[北京师范大学][2] 读书，我们在[北京大学][3] 上课时认识。
[1]: www.bupt.edu.cn "北邮"
[2]: www.bnu.edu.cn "北师大"
[3]: www.pku.edu.cn "北大"
```

效果：  
我在[北京邮电大学][1] 读书，女朋友在[北京师范大学][2] 读书，我们在[北京大学][3] 上课时认识。
[1]: www.bupt.edu.cn "北邮"
[2]: www.bnu.edu.cn "北师大"
[3]: www.pku.edu.cn "北大"

自动链接：  
Markdown支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要使用<>包起来，Markdown就会自动把它转为链接。  
代码：  
```markdwon
<http://www.bupt.edu.cn>
<wangdachui@bupt.edu.cn>
```
效果：
<http://www.bupt.edu.cn>
<wangdachui@bupt.edu.cn>

### 2.6 插入图片
图片的语法类似链接。alt text是替换文本；在图像无法显示时才呈现出来。  
行内形式：  

代码：
```markdown
![alt text](https://pic1.zhimg.com/80/v2-de2e829ad6b60930009b8bd1eb05057c_hd.jpg "图片")
```

效果：  
![alt text](https://pic1.zhimg.com/80/v2-de2e829ad6b60930009b8bd1eb05057c_hd.jpg "图片")

参考形式：   
代码：
```markdown
![alt text][id]
[id]: https://pic1.zhimg.com/80/v2-de2e829ad6b60930009b8bd1eb05057c_hd.jpg "图片"
```

效果：  
![alt text][1]
[1]: https://pic1.zhimg.com/80/v2-de2e829ad6b60930009b8bd1eb05057c_hd.jpg "图片"  

### 2.7 列表
**无序列表**  
使用星号 * 、加号 + 或是减号 -做标记。 标记符号后面一定要接着至少一个空格或制表符。  
代码：  
```markdown
- 减号
+ 加号
* 乘号
```
效果：  

- 减号
+ 加号
* 乘号
无序列表标记符前每增加四个空格，增加一个层级：
```markdown
- 第一层级
    - 第二层级
      - 第三层级
```

效果：    

- 第一层级  
    - 第二层级  
        - 第三层级  

**有序列表**
使用数字接着一个英文句点。标记符号后面也要接着至少一个空格或制表符(Tab)。  
代码：  
```markdown
1. 序号1
2. 序号2
3. 序号3
```

效果：   

1. 序号1
2. 序号2
3. 序号3


## ３. 常用快捷键
### 3.1 shift+space 
输入法切换为全角模式，输入空格缩进时常用
鼠标选中多行，按下 Ctrl Shift L (Command Shift L) 即可同时编辑这些行；
鼠标选中文本，反复按 CTRL D (Command D) 即可继续向下同时选中下一个相同的文本进行同时编辑；
鼠标选中文本，按下 Alt F3 (Win) 或 Ctrl Command G(Mac) 即可一次性选择全部的相同文本进行同时编辑；
Shift 鼠标右键 (Win) 或 Option 鼠标左键 (Mac) 或使用鼠标中键可以用鼠标进行竖向多行选择；
Ctrl 鼠标左键(Win) 或 Command 鼠标左键(Mac) 可以手动选择同时要编辑。
ctrl+k+u 小写转大写
ctrl+k+l 大写转小写
ctrl+insert 复制这一行
shift+insert 插入复制的行

## 4. 常见问题
### 4.1 Sublime Text 不能被设置为默认打开方式
可能是因为卸载了旧版本的Sublime Text2，并且重新安装了的Sublime Text3，导致无法选择将 Sublime Text设置为默认打开方式。解决方法：  
1. 打开注册表： `win+R 输入 regedit`   
2. 找到 `HKEY_CLASSES_ROOT\Applications\sublime_text.exe\shell\open\command`   
3. 打开 `command` 修改数据里面的路径名称，我这里面的值还为原来 `Sublime Text2`的安装路径，更改为新的路径。

### 4.2 设置Sublime Text为右键选择项目
1. cmd->regedit 打开注册表
2. 在 计算机\HKEY_CLASSES_ROOT\*\shell 下面添加项Edit with Sublime 然后在该项下，添加字符串Icon，其数值数据设置为"C:\Program Files\Sublime Text 3\sublime_text.exe,0" ，sublime.exe的本地安装位置。
3. 然后在 Edit with Sublime 继续新建项目Command,Command项目下默认值修改为"C:\Program Files\Sublime Text 3\sublime_text.exe %1"。设置完成后，确定退出。现在右键菜单栏中就有了。
