# spring框架
![](https://i.imgur.com/ejtl7Eg.jpg)
##1、Spring IOC、AOP的理解和实现的原理，有哪些实现方式。
-  IOC:反转控制 ,创建对象的方式反转了,从自己创建变成了spring容器
-  DI(具体的技术):依赖注入,将必须的属性注入到对象当中，是实现ioc思想必须条件。
   ![](https://i.imgur.com/lHWxT9C.jpg)
-   AOP:面向切面编程(**横向重复、纵向抽取**)
    ![](https://i.imgur.com/EHs6Iyf.jpg)
    ![](https://i.imgur.com/yRkPwxf.jpg)
    ![](https://i.imgur.com/bC7ZALe.jpg)
    ![](https://i.imgur.com/cLRu2Oc.jpg)
##2、IOC容器的加载过程。

## 3、动态代理和cglib思想的区别。

##4、Hibernate一级缓存和二级缓存之间的区别。

##5、Spring MVC的原理。

##6、Hibernate常见的优化策略。

##7、Hibernate和mybatis的区别。

##8、Spring中autowire和resourse关键字的区别。
     都是实现对象类型的注入
##9、如何实现autowire注解的功能。
     自动装配:实现对象类型的注入

##10.Spring的属性(Bean)创建与注入:
  ![](https://i.imgur.com/Jf1BrXp.jpg)
###创建:
    ** (1)空参构造创建**
     (2)静态工厂
     (3)实例工厂 

###注入:
     **(1)set方法注入**
     **(2)构造函数注入**
      (3)p名称空间注入
      (4)spel注入