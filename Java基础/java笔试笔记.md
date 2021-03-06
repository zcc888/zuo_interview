# Java笔试基础

##(1)Java标识符由**数字、字母、下划线(_)、美元符号($)或人民币(¥)组成，首位不能是数字**。并且Java关键字不能作为标识符。

##(2)==可用于基本类型和引用类型：当用于基本类型时候，是比较值是否相同；当用于引用类型的时候，是比较对象是否相同。"=="和"!="比较的是地址 指第一个new()c出来的地址,所以因为两次new() 分出的内存也不同


##(3)运算符优先级 （口诀：淡云一笔安洛三福 单目>算数运算符>移位>比较>按位>逻辑>三目>赋值）
- 单目运算符：+，-，++，--
- 算数运算符：+，-，*，/，%
- 移位运算符：<<,>>
- 关系运算符：>,<,>=,<=,==,!=
- 位运算符：&，|，~，^,
- 逻辑运算符：&&，||
- 三目运算符：表达式1？表达式2：表达式3;
- 赋值运算符：=等

##(4)反射机制
1. public Method[] getDeclaredMethods()返回类或接口声明的所有方法，包括public, protected, default (package) 访问和private方法的Method对象，但不包括继承的方法。当然也包括它所实现接口的方法。
2. public Method[] getMethods()返回类的所有public方法，包括其继承类的公用方法，当然也包括它所实现接口的方法。

##(5)方法存储位置
  方法通常存储在**进程**中的**方法区**(
一条进程的栈区、堆区、数据区和代码区在内存中的映射 
    1>栈区：主要用来存放局部变量, 传递参数, 存放函数的返回地址。.esp 始终指向栈顶, 栈中的数据越多, esp的值越小。 
    2>堆区：用于存放动态分配的对象, 当你使用 malloc和new 等进行分配时,所得到的空间就在堆中。动态分配得到的内存区域附带有分配信息, 所以你　 能够 free和delete它们。 
    3>数据区：全局，静态和常量是分配在数据区中的，数据区包括bss（未初始化数据区）和初始化数据区。)

##(6)抽象类可以有普通的成员变量，接口中也可以有成员变量，但必须用public static final.抽象类可以有private的成员,abstract 方法必须在abstract类或接口中。
   ![](https://i.imgur.com/S6oCCIw.jpg)

##(7)Java表达式转型规则由低到高转换：

- 
-  byte b1=1,b2=2,b3,b6,b8;
-  final byte b4=4,b5=6,b7;
-   b3=(b1+b2);  /*语句1*/
-   b6=b4+b5;    /*语句2*/
-  b8=(b1+b4);  /*语句3*/
-  b7=(b2+b5);  /*语句4*/
-   System.out.println(b3+b6);
-  下列代码片段中，存在编译错误的语句是()

- 1、所有的byte,short,char型的值将被提升为int型；
- 2、如果有一个操作数是long型，计算结果是long型；
- 3、如果有一个操作数是float型，计算结果是float型；
- 4、如果有一个操作数是double型，计算结果是double型；
- 5、被fianl修饰的变量不会自动改变类型，当2个final修饰相操作时，结果会根据左边变量的类型而转化。
- --------------解析--------------
- 语句1错误：b3=(b1+b2);自动转为int，所以正确写法为b3=(byte)(b1+b2);或者将b3定义为int；
- 语句2正确：b6=b4+b5;b4、b5为final类型，不会自动提升，所以和的类型视左边变量类型而定，即b6可以是任意数值类型；
- 语句3错误：b8=(b1+b4);虽然b4不会自动提升，但b1仍会自动提升，所以结果需要强转，b8=(byte)(b1+b4);
- 语句4错误：b7=(b2+b5); 同上。同时注意b7是final修饰，即只可赋值一次，便不可再改变。
- 
##(8)实现接口，就要实现接口的所有方法，相当于重写方法，方法的重写需要满足：三同一大一小（方法名、返回值类型、形参相同；访问权限>=重写前；抛出异常<=重写前）

##(9)[SpringMVC](https://www.jianshu.com/p/ca5d246761cd)
  ![](https://i.imgur.com/oO2dYZF.png)
##（10）java异常机制
 ![](https://i.imgur.com/q22Peu4.jpg)
![](https://i.imgur.com/LUgNwlI.jpg)

##(10)WEB开发中实现会话跟踪实现
 HTTP是一种无状态协议，每当用户发出请求时，服务器就会做出响应，客户端与服务器之间的联系是离散的、非连续的。当用户在同一网站的多个页面之间转换时，根本无法确定是否是同一个客户，会话跟踪技术就可以解决这个问题。当一个客户在多个页面间切换时，服务器会保存该用户的信息。

有四种方法可以实现会话跟踪技术：**URL重写、隐藏表单域、Cookie、Session**。

1）.隐藏表单域：<input type="hidden">，非常适合不需要大量数据存储的会话应用。
2）.URL 重写:URL 可以在后面附加参数，和服务器的请求一起发送，这些参数为名字/值对。
3）.Cookie:一个 Cookie 是一个小的，已命名数据元素。服务器使用 SET-Cookie 头标将它作为 HTTP
响应的一部分传送到客户端，客户端被请求保存 Cookie 值，在对同一服务器的后续请求使用一个
Cookie 头标将之返回到服务器。与其它技术比较，Cookie 的一个优点是在浏览器会话结束后，甚至
在客户端计算机重启后它仍可以保留其值
4）.Session：使用 setAttribute(String str,Object obj)方法将对象捆绑到一个会话

##(11)Java中的8种基本类型属于原生类，而数组是引用类型，不属于原生类，可以看成是一种对象。
![](https://i.imgur.com/wPnWuXM.png)
![](https://i.imgur.com/p4ERds9.jpg)

##(12)进制转换（1*n+3）*(1*n+4)=2*n^2+4;//    n=-1或n=8;  其中n=8成立
![](https://i.imgur.com/oktY4hD.jpg)

##(13)instance是java的二元运算符，用来判断他左边的对象是否为右面类（接口，抽象类，父类）的实例

##(14)赋值运算是有返回值的，赋了什么值，就返回什么值
![](https://i.imgur.com/ncfGNpw.jpg)
##(15)接口和抽象类的区别
![](https://i.imgur.com/DVxEtlC.jpg)

##(16)java ++特性
![](https://i.imgur.com/57vtlGl.jpg)
 count = count++  原理是 temp = count； count = count+1 ； count = temp；   因此count始终是0 这仅限于java ,c,c++是不一样的

##(17)[final ,finally等](https://www.nowcoder.com/test/question/done?tid=16379875&qid=14305#summary)
![](https://i.imgur.com/qW2Nkxj.jpg)

##(18)[经典题型](https://www.nowcoder.com/test/question/done?tid=16379875&qid=55361#summary)

##(19)计算弧度值
 ![](https://i.imgur.com/810SQY9.jpg)
##(20)[索引的运用](https://www.nowcoder.com/questionTerminal/7d2af51194e14e708c71c855f5f28a36)
![](https://i.imgur.com/x12Vp5C.jpg)

##(21)[语句声明](https://www.nowcoder.com/test/question/done?tid=16380309&qid=56003#summary)

##(22)字符串的编码
![](https://i.imgur.com/O4PEu87.jpg)
##(23)字符串操作
![](https://i.imgur.com/NR2sLXW.jpg)
##(24)运算符的优先级
![](https://i.imgur.com/yNlrp1J.jpg)