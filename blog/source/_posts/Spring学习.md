---
title: Spring学习
date: 2020-01-07 22:54:16
tags: "Java"
categories: "编程"
---
### Spring对象的创建和依赖关系维护
面向切面编程AOP
IOC底层原理
面向接口编程：
第一阶段：UserService us = new UserSeervice();s//定义类和创建类对象
第二阶段：面向接口编程
UserService[这是个接口] us = new UserServiceImp()【接口实现】; //这就是耦合，因为如果要换一个实现，就要修改此处代码
第三阶段：
ocp原则，open-close原则，对程序扩展时open的，对修改程序代码是close。尽量不修改程序的源码，实现对程序的扩展。
使用工厂模式，工厂类创建实例对象。
Class FactoryBean{
    public UserService getUs(){
        return new UserServiceImp();
    }
}
UserService us = FactoryBean.getUs();//这样可以使UserService us和UserServiceImp解耦合，但是UserService却又和FactoryBean耦合了。
第四阶段：工厂+反射+配置文件
<bean id="us" class = "com.clcun.UserServiceImpl"/>
class FactoryBean{
    public static Object getBean(String id)
    {
        //根据id 找到class 然后反射创建Class类
    }
}