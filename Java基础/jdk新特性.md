#[jdk的新特性](https://blog.csdn.net/zuochao_2013/article/details/80393943)


#[java 7,8,9,10的对比](https://blog.csdn.net/ttkatrina/article/details/79646874)
##一、Java 7的那些语法糖
- 1.switch可以接受string类型而不像以前仅仅是int；
-  
- 2.异常catch可以一次处理完而不像以前一层层的surround；
-  
- 3.泛型类实例化也不用繁琐的将泛型声明再写一遍； 
- 
- 4.文件读写 会自动关闭流而不像以前那样需要在finally中显式close； 
- 
- 5.数值可以使用下划线分隔； 
- 
- 6.文件读写功能增强，有更简单的api调用；（Path path = Paths.get(“c:\Temp\temp”); Files.deleteIfExists(path); ）
-  
- 7.文件改变的事件通知功能；(watchService = FileSystems.getDefault().newWatchService()) 
- 
- 8.多核 并行计算的支持加强 fork join 框架；(ForkJoinPool pool = new ForkJoinPool(numberOfProcessors); ) 
- 
- 9.还有一些动态特性的加入。(java.lang.invoke 包的引入。 MethodHandle, CallSite 还有一些其他类供使用。)
- 

##二、Java8新特性详解
- 1.接口的默认方法，在接口中新增了default方法和static方法，这两种方法可以有方法体；接口里的静态方法，即static修饰的有方法体的方法不会被继承或者实现，但是静态变量会被继承。结论：接口中的static方法不能被继承，也不能被实现类调用，只能被自身调用。default方法可以被子接口继承亦可被其实现类所调用；default方法被继承时，可以被子接口覆写 
- 
- 2.Lambda表达式可以看成是匿名内部类，使用Lambda表达式时，接口必须是函数式接口；
-  
- 基本语法：
  
> **<函数式接口>  <变量名> = (参数1，参数2...) -> {
                    //方法体
    }**

说明： 
(参数1，参数2…)表示参数列表；->表示连接符；{}内部是方法体 
- 1、=右边的类型会根据左边的函数式接口类型自动推断； 
- 
- 2、如果形参列表为空，只需保留()； 
- 
- 3、如果形参只有1个，()可以省略，只需要参数的名称即可； 
- 
- 4、如果执行语句只有1句，且无返回值，{}可以省略，若有返回值，则若想省去{}，则必须同时省略return，且执行语句也保证只有1句； 
- 
- 5、形参列表的数据类型会自动推断； 
- 
- 6、lambda不会生成一个单独的内部类文件； 
- 
- 7、lambda表达式若访问了局部变量，则局部变量必须是final的，若是局部变量没有加final关键字，系统会自动添加，此后在修改该局部变量，会报错；
- 
- 3.如果一个接口只有一个抽象方法，则该接口称之为函数式接口，因为 默认方法 不算抽象方法，所以你也可以给你的函数式接口添加默认方法。 
- 
- 函数式接口可以使用Lambda表达式，lambda表达式会被匹配到这个抽象方法上 ; 
- 我们可以将lambda表达式当作任意只包含一个抽象方法的接口类型，确保你的接口一定达到这个要求，你只需要给你的接口添加@FunctionalInterface 注解，编译器如果发现你标注了这个注解的接口有多于一个抽象方法的时候会报错的 
- 
- 5.作用域：在lambda表达式中访问外层作用域和老版本的匿名对象中的方式很相似。你可以直接访问标记了final的外层局部变量，或者实例的字段以及静态变量。
-  
- 6.我们可以直接在lambda表达式中访问外层的局部变量，但是该局部变量必须是final的，即使没有加final关键字，之后我们无论在哪（lambda表达式内部或外部）修改该变量，均报错。
-  
- 7.访问对象字段与静态变量，lambda内部对于实例的字段以及静态变量是即可读又可写。该行为和匿名对象是一致的； 
- 
- 8.访问接口的默认方法：Predicate接口，Function接口，Supplier接口，Consumer 接口，Comparator 接口，Optional 接口。 
- 
- Stream 接口 重要！！！创建stream–通过of方法, 通过generator方法。 
- 
- 9.Date API: Java 8 在包java.time下包含了一组全新的时间日期API。Clock时钟，Timezones时区，LocalTime本地时间，LocalDate本地日期，LocalDateTime 本地日期时间 。DayOfWeek… 只要附加上时区信息，就可以将其转换为一个时间点Instant对象，Instant时间点对象可以很容易的转换为老式的java.util.Date。 
- 
- 10.Annotation 注解 
- 
- 在Java 8中支持多重注解了
- 
##三、java9新特性
- (1)Jshell
- 
- (2)模块化(Jigsaw)
- 
- (3)轻量级JSON API
- 
- (4)简化了进程API
- 
- (5)代码分段缓存
- 
- (6)接口私有方法
- 
- (7)响应式编程
- 
- (8)集合工场方法
- 
- (9)Stream API
- 
-（10）Java 9 移除了在 Java 8 中 被废弃的垃圾回收器配置组合，同时把G1设为默认的垃圾回收器实现。替代了之前默认使用的Parallel GC
- 
