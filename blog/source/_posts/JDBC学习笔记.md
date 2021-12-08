---
title: JDBC学习笔记
date: 2020-05-16 00:26:38
tags: "Java"
categories: "编程"
---
### DriverManager 作用：
1、注册驱动；
DriverManager.registerDriver(new Driver());//加载驱动，这种方法会导致驱动注册两次
Class.forName("com.mysql.cj.jdbc.Driver");//常用这种
2、获取连接；
Connection connection = DriverManager.getConnection(url,username,password);
### Connection：连接对象 作用：
1. 创建执行SQL语句的对象
Statement stmt = connection.createStatement();
//参数化语句发送给数据库，预编译语句
PreparedStatement ps = connection.prepareStatement(sqlSelect);
//调用数据库存储过程
CallableStatement cs = connection.prepareCall(sqlSelect);
2. 事务管理
connection.setAutoCommit(false);//将不自动提交事务，需要手动提交；在此期间所作的多个操作，一起成功或者一起失败
connection.commit();//事务提交
connection.rollback();//事务回滚
### Statement 执行sql语句
boolean searchresult = stmt.execute(sqlSelect);