---
title: Mysql学习笔记
date: 2020-03-06 19:09:50
tags: "Mysql"
categories: "数据库"
---
##简介
DataBaseSystem： 数据库、数据库管理系统（DBMS）、应用开发工具
sql语言：DDL 数据定义 DML 数据操作 增删改 DCL数据控制 用户授权等 DQL 查询语言
mysql配置文件位置C:\ProgramData\MySQL\MySQL Server 8.0\my.ini

通过命令行连接数据库
mysql -uroot -p
退出 exit 或者 quit 或者\q

获取版本mysql --version 或 mysql -V
登录的同时打开指定数据库mysql -uroot -p -D db_name
查看已经有的数据库show databases
使用use命令打开指定的mydatabase数据库
登陆进入指定数据库后，查看是否登入成功,查看当前数据库 select database();

命令行结束符默认是;或者\g
查看当前版本号select version();
查看当前用户select user();
查看当前时间 select now();
help或者\h 是帮助手册
help create database
\c 取消当前命令的执行

建议写法：
库名 表名 字段名 小写
关键字大写

##数据库操作DDL
create database或者schema db_name;
show databases 或者 show schemas
检测数据库名称是否存在，不存在则创建
create database if not exists db_name;

查看上一步操作产生的警告信息show warnings;
创建数据库同时指定编码方式：
create database if not exists db_name [default] character set[=] charset;
create database if not exists test1 default character  set 'utf8';
create database if not exists test1 default character  set 'gbk';

查看指定数据库的详细信息：
show create database db_name;
修改数据库编码方式：
alter database db_name default character set[=] charset;

打开指定数据库 use db_name; 
删除指定数据库drop database db_name;
drop database if  exists db_name;
注释用#或者--


##数据表相关操作
创建数据表
create table [if not exists] tbl_name(字段名称 字段类型[完整性约束条件], 字段名称 字段类型[完整性约束条件])ENGINE=存储引擎 CHARSET=编码方式;
mysql中的数据类型：
整数类型 tinyint smallint mediumint int bigint bool boolean
浮点数
float(m,d) 4个字节 m数字总位数，d是小数点后面的位数 单精度 
double 8个字节双精度

定点数 decimal 和double一样，内部以字符串形式存储数值，更精准，长度是M+2
 
字符串 char(m) 定长 varchar(m) 变长
char 比varchar浪费空间，但查询速度会快
 tinytext text mediumtext longtext enum 枚举类型 
日期时间类型
time  3个字节
date 日期 3个字节
datetime 日期加时间 8个字节
timestamp 时间戳 4个字节
year 1个字节
select now();
select current_time;


show tables; 查看数据库下的表
?show tables; 查看使用手册

show full tables from/in db_name;
//查看指定数据表的指定详细信息
show create table tbl_name;
show create table user;
查看表结构
desc tbl_name;
describle tbl_name;
show columns from tbl_name;

删除指定数据表
drop table if exists db_name;
建表的时候使用的完整性约束条件：
unsighed 无符号
zerofill 零填充 当显示长度不够的时候可以使用前补0的效果填充至指定长度；
not null 非空约束，插入时候这个字段必须有值
default 默认值，如果插入时没有赋值，就用这个值
primary key 主键，标识记录的唯一性，值不能重复
unique key 唯一性，一个表中可以有多个字段时唯一索引，值不能重复，但是null除外
auto_increment 自动增长，只能用于数值列，而且配合索引所有
foreign key 外键约束


添加字段和删除字段
alter table table_name add 字段名称 字段属性 [完整性约束] [first|after 字段名]
alter table table_name drop 字段名称

添加多行删除多行同时操作
```sql
alter table user1 
add address varchar(20),
add age int unsigned not null default 18,
drop email;
```

添加和删除默认值操作
alter table table_name 
alter 字段名称 set default 默认值;

alter table table_name 
alter 字段名称 drop default;

修改字段类型和字段属性：alter table table_name modify 字段名称 字段类型[字段属性][first|after字段名称]

修改字段名称、字段类型、字段属性
alter table table_name change 原字段名称 新字段名称 字段类型 字段属性[first|after 字段名称]

添加主键和删除主键
alter table table_name add primary key(字段名称);
alter table table_name drop primary key;
--对于有auto_increment的主键，将id的auto_increment去掉，然后才可以删除主键
alter table user3 modify id int unsigned;
alter table user3 change id id int unsigned;

--添加唯一和删除唯一
alter table table_name add unique key|index index_name(字段名称);
alter table table_name drop index index_name;

--修改数据表名称
alter table table_name rename [to|as] new_table_name;
rename table table_name to new_table_name;

--存储引擎
MyISAM存储引擎
create table if not EXISTS user5(
id int unsigned ,
username varchar(20) not null unique,
age int unsigned not null default 18,
email varchar(50) not null unique
) EN;
会在磁盘中产生三个文件：
frm 表结构文件
myd 存储数据的文件
myi 索引文件
可以在建表时指定数据文件和索引文件的存储位置
data direcory [=] 数据保存的绝对路径
index directory[=] 索引文件保存的绝对路径
单表最大支持的数据量2^64
每个表最多可以建64个索引，复合索引最多包含16个字段


InnoDB存储引擎：ACID模型原子性一致性隔离性持久性，支持事务，从服务崩溃中恢复的能力
支持行级锁，当用户多并发时的性能提高
支持外键，保证数据一致性和完整性
拥有缓冲池，索引等存放在缓存中。
insert update delete操作会使用change buffering自动优化，提供一致性的读取，缓存变更数据，减少磁盘I/O，提高性能。
frm表结构文件
ibd 表空间文件，数据和索引存储在表空间中
所有表最好都创建主键，可以放到经常查询的列作为主键。

--数据操作
添加记录
insert [into] tb_name[(col_name,。。。)] {value|values}(...);
insert tb_name value(...);按照建表时字段顺序，添加记录
一次添加多条记录
insert tb_name[(字段名称,...)] values(值1,...),(值2,...), (值3,...);

insert table_name set 字段名称=值,...;
insert table_name(字段名称) select(字段名称) from。。。；
修改记录
update test_add set username='gt', age = 19 where id = 1;
删除记录
delete from test_add where id = 5;
            --重置auto_increment
            alter table test_add auto_increment = 1;
彻底清空 truncate [table] table_name; 可以把auto_increment 清空
查看记录
select ... from table_name where .. group by .. having .. order by .. asc|desc limit 限制结果集显示条数


select u1.user_id as '编号' from user as u1;

where条件：
<=>null is null 两种方式检测null
% 任意长度的字符串 _任意一个字符


select id ,username from test_add group by sex;

分组配合group_concat()查看某个字段的详细信息   
select group_concat(username), id, age, email from user group by age ;

配合聚合函数
count sum max min avg 

select count(*) as total_count from user;