# 框架

#[duboo架构](https://blog.csdn.net/zuochao_2013/article/details/80639997)

#[官方文档](http://dubbo.apache.org/books/dubbo-user-book/)

# [开发文档](http://dubbo.apache.org/books/dubbo-dev-book/)

![](http://shiyanjuncn.b0.upaiyun.com/wp-content/uploads/2013/09/dubbo-relation.png)

# 一、什么是dubbo
**Dubbo是一个高性能服务框架，致力于提供高性能和透明化的RPC远程服务调用方案，以及SOA服务治理方案，使得应用可通过高性能RPC实现服务的输出和输入功能，和Spring框架可以无缝集成。**Dubbo是Alibaba开源的分布式服务框架，它最大的特点是按照分层的方式来架构，使用这种方式可以使各个层之间解耦合（或者最大限度地松耦合）。从服务模型的角度来看，Dubbo采用的是一种非常简单的模型，要么是提供方提供服务，要么是消费方消费服务，所以基于这一点可以抽象出服务提供方（Provider）和服务消费方（Consumer）两个角色。
**Dubbo其功能主要包括**：高性能NIO通讯及多协议集成，服务动态寻址与路由，软负载均衡与容错，依赖分析与服务降级等。
**Dubbo最大的特点**是按照分层的方式来架构，使用这种方式可以使各个层之间解耦合（或者最大限度地松耦合）。从服务模型的角度来看，Dubbo采用的是一种非常简单的模型，要么是提供方提供服务，要么是消费方消费服务，所以基于这一点可以抽象出服务提供方（Provider）和服务消费方（Consumer）两个角色。

**Dubbo包含<font color="#dd0000">远程通讯、集群容错和自动发现</font>三个核心部分.**
# 二、Dubbo的总体架构
![](https://i.imgur.com/QuQ4J1o.png)
![](https://i.imgur.com/IbkSVT3.png)
调用关系说明：

>0.服务容器负责启动，加载，运行服务提供者。

>1.服务提供者在启动时，向注册中心注册自己提供的服务。

>2.服务消费者在启动时，向注册中心订阅自己所需的服务。

>3.注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者。

>4.服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用。

>5.服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心。

![](https://i.imgur.com/eJ5nx4F.png)
各层说明：
Dubbo框架设计共划分了10层，最上面的**Service层**是留给实际使用Dubbo开发分布式服务的开发者实现业务逻辑的接口层。图中左边淡蓝背景的为服务消费方使用的接口，右边淡绿色背景的为服务提供方使用的接口，位于中轴线上的为双方都用到的接口。

**Config配置层**：对外配置接口，以ServiceConfig、ReferenceConfig为中心，可以直接初始化配置类，也可以通过Spring解析配置生成配置类。

**Proxy服务代理层**：服务接口透明代理，生成服务的客户端Stub和服务器端Skeleton，以ServiceProxy为中心，扩展接口为ProxyFactory。

**Registry注册中心层**：封装服务地址的注册与发现，以服务URL为中心，扩展接口为RegistryFactory、Registry、RegistryService。

**Cluster路由层**：封装多个提供者的路由及负载均衡，并桥接注册中心，以Invoker为中心，扩展接口为Cluster、Directory、Router、LoadBalance。

**Monitor监控层**：RPC调用次数和调用时间监控，以Statistics为中心，扩展接口为MonitorFactory、Monitor、MonitorService。

**Protocol远程调用层**：封将RPC调用，以Invocation、Result为中心，扩展接口为Protocol、Invoker、Exporter。

**Exchange信息交换层**：封装请求响应模式，同步转异步，以Request、Response为中心，扩展接口为Exchanger、ExchangeChannel、ExchangeClient、ExchangeServer。

**Transport网络传输层**：抽象MINA和Netty为统一接口，以Message为中心，扩展接口为Channel、Transporter、Client、Server、Codec。

**Serialize数据序列化层**：可复用的一些工具，扩展接口为Serialization、ObjectInput、ObjectOutput、ThreadPool。

