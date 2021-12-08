---
title: idea使用指南
date: 2019-12-12 15:51:12
tags: "idea"
categories: "工具"
---
## 快捷键
1. ctrl+alt+s 调出settings面板:Editor->General->CodeCompletion->Match case 勾选去掉，可以将自动提示的大小写匹配去掉;KeyMap->MainMenu->Code->Completion->Basic可以设置智能提示，比如设置为ctrl+j
2. 自动生成get和set alt + insert 键 ctrl + a 选中所有属性
3. ctrl+shift+a 调出查找面板 然后输入constructor 
4. ctrl+左右箭头 跳转完整的单词
5. ctrl+shift+enter 自动完成当前行 加上分号或者换行
6. alt+insert generate constructor getter setter
7. ctrl+insert 复制当前行
8. ctrl+alt+l 格式化代码
9. ctrl+shift+/ 注释
10. ctrl+alt+shift+j 列操作 一次性把当前文件所有同名的单词或者句子选中，进行修改
11. shift+f6  重命名 选择后按shift+f6 只对修改有影响的所有变量进行修改
12. ctrl+w 选中单词
13. ctrl+shift+f/r 全局查找和替换
14. ctrl+shift+n 文件查找面板
15. sout live template
16. 输入new ArrayList<>(); 按ctrl+alt+v 自动定义变量如下
        ArrayList<String> strings = new ArrayList<>();
17. ctrl + shift+f10 运行程序
18. ctrl+e 最近访问的文件列表
19. ctrl+shift+e 最近编辑过的文件
20. ctrl+shift+1-9 创建书签
21. shift+f11 查看所有书签
22. ctrl+1-9 切换书签
23. alt + 左右箭头 切换页签
24. ctrl+g 跳转到行
25. //模板live template
    //psvm 
    //sout
    //psfs
    //fori
    //itli
26. shift+f9 调试
27. shift+f10 运行
28. shift+ctrl+f8 查看所有断点
29. f8 单步运行 f9恢复运行至下一个断点
30. ctrl+alt+enter 上方插入行
31. shift+enter 下方插入行
32. ctrl+alt+v 自动抽取并生成变量
33. clt+enter show context actions 比如添加try catch等
34. ctrl+alt+j surround with live complate
35. ctrl_alt+t surround with while if try catch
36. alt+shift+enter 导入包 完成接口方法
37. alt+o override method 
38. Ctrl+”+/-”,当前方法展开、折叠
39. Ctrl+Shift+”+/-”,全部展开、折叠

##常见问题
###web目录下创建一个文件夹，无法自动更新到out\artifacts
在web中创建任意一个jsp文件，在项目编译运行后，都会自动更新到out\artifacts\ ，当创建空文件夹却无法自动更新。可以在里面放一个无关的空文件。
###编译调试时存放的临时tomcat目录：
C:\Users\gaota\.IntelliJIdea2019.2\system\tomcat\Tomcat_9_0_27_jquery