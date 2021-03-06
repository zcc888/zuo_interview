# 计算机网络

# 1、如何保存会话状态，有哪些方式和区别。
 > session(服务器端)
 > 
 > cookie(客户端)
# 2、[cookie和session的区别](https://blog.csdn.net/zuochao_2013/article/details/80139900)
- 1，session 在服务器端，cookie 在客户端（浏览器）
- 2，session 默认被存在在服务器的一个文件里（不是内存）
- 3，session 的运行依赖 session id，而 session id 是存在 cookie 中的，也就是说，如果浏览器禁用了 cookie ，同时 session 也会失效（但是可以通过其它方式实现，比如在 url 中传递 session_id）
- 4，session 可以放在 文件、数据库、或内存中都可以。
- 5，用户验证这种场合一般会用 session

# 3、[HTTP和HTTPS的区别](https://blog.csdn.net/zuochao_2013/article/details/79933461)？

# 4、HTTP1.0和HTTP1.1、HTTP2.0的区别？
>**HTTP1.1与HTTP 1.0的主要区别** 

 >**(1)长连接**
 >
 HTTP 1.0需要使用keep-alive参数来告知服务器端要建立一个长连接，而HTTP1.1默认支持长连接。

 >**(2)节约带宽**
 >
 >HTTP 1.1支持只发送header信息(不带任何body信息)，如果服务器认为客户端有权限请求服务器，则返回100，否则返回401。客户端如果接收到100，才开始把请求body发送到服务器。
 
 >**(3)HOST域**
 >
 >web server上的多个虚拟站点可以共享同一个ip和端口。

>**HTTP1.1与HTTP 2.0的主要区别**

>**(1)多路复用**
>
>允许同时通过单一的 HTTP/2 连接发起多重的请求-响应消息。众所周知，在HTTP/1.1协议中，浏览器客户端在同一时间针对同一域名的请求有一定数据限制。超过限制数目的请求会被阻塞。HTTP2.0使用了**多路复用**的技术，做到同一个连接并发处理多个请求，而且并发请求的数量比HTTP1.1大了好几个数量级。

>**(2)二进制分帧**
>
>HTTP 2.0在应用层（HTTP/2）和传输层（TCP or UDP）之间增加一个二进制分帧层。

>**(3)首部压缩**
>
>HTTP1.1不支持header数据的压缩，HTTP2.0使用HPACK算法对header的数据进行压缩，这样数据体积小了，在网络上传输就会更快。

>**(4)服务器推送**
>
>服务端推送是一种在客户端请求之前发送数据的机制。

>**(5)在HTTP/2中，服务器可以对客户端的一个请求发送多个响应。**

 ![](http://mmbiz.qpic.cn/mmbiz_png/cmOLumrNib1cfBOtIMQ6JfSibJdd6QkQribgQuEeJaevuN9LRgQ9WR85hRiaVISeia7SDz1aU9hAAgO33XFaJ3FhmhQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1)
 ![](https://i.imgur.com/ZbNrDNJ.png)

# 5、[TCP如何保证可靠传输](https://www.cnblogs.com/deliver/p/5471231.html)？
- 1、确认和重传(滑动窗口)：接收方收到报文就会确认，发送方发送一段时间后没有收到确认就重传。
- 
- 2、数据校验
- 
- 3、数据合理分片和排序：
- 
- 　　UDP：IP数据报大于1500字节,大于MTU.这个时候发送方IP层就需要分片(fragmentation).把数据报分成若干片,使每一片都小于MTU.而接收方IP层则需要进行数据报的重组.这样就会多做许多事情,而更严重的是,由于UDP的特性,当某一片数据传送中丢失时,接收方便无法重组数据报.将导致丢弃整个UDP数据报.
- 
- 　　tcp会按MTU合理分片，接收方会缓存未按序到达的数据，重新排序后再交给应用层。
- 
- 4、流量控制：当接收方来不及处理发送方的数据，能提示发送方降低发送的速率，防止包丢失。
- 
- 5、拥塞控制：当网络拥塞时，减少数据的发送。
- 
![](https://images2015.cnblogs.com/blog/476810/201605/476810-20160508191022499-1268503427.jpg)

# 6、TCP的三次握手，四次挥手是什么？

# 7、为何TCP需要三次握手？两次不可以吗？

# 8、为何TCP需要四次挥手？三次不可以吗？

# 9、time_out的时候是多少？
 > session 默认30分钟
 
# 10、如果客户端不断发送请求连接会怎么样？

# 11、[GET和POST的区别](https://blog.csdn.net/zuochao_2013/article/details/79522926)？

# 12、TCP和UDP的区别。

# 13、TCP的拥塞处理。

# 14、从输入网址到获得页面的过程。

# 15、Forward和redirect的区别。

# 16、怎么解决session一致性缓存的问题。

# 17、反爬虫的机制，有哪些方式。

# 18、socket编程的理解。

# 19、Channel和buffer的区别。

# 20、directBuffer和buffer的区别。

# 21、http协议的chunk。

# 22、http的状态码。404，301与302的区别。502和503的区别。
  >301（永久性重定向）302(临时性重定向)
  >
  >404(找不到文件:(1)服务器上无法找到请求的资源 (2服务器拒绝请求)
  >
  >500(服务器内部错误:(1)服务器内部执行时发生错误 (2)web应用存在bug)
  >502(错误网关)  503（服务不可用:服务器由于超负载等进行维护）
  
<table>
        <tr>
            <th></th>
            <th>类别</th>
            <th>原因短语</th>
      
        </tr>
        <tr>
            <th>1XX</th>
            <th>Information(信息性状态码)</th>
            <th>接受的请求正在处理</th>
           
        </tr>
        <tr>
            <th>2XX</th>
            <th>Success(成功状态码)</th>
            <th>请求正常处理完毕</th>
        </tr>
        <tr>
            <th>3XX</th>
            <th>Redirection(重定向状态码)</th>
            <th>需要进行附加操作以完成请求</th>
        </tr>
         <tr>
            <th>4XX</th>
            <th>Client Error(客户端错误状态码)</th>
            <th>服务器无法处理请求</th>
        </tr>
        <tr>
            <th>5XX</th>
            <th>Server Error(服务器错误状态码)</th>
            <th>服务器处理请求出错</th>
        </tr>
 </table>

# 23、如何理解长连接、短连接？

>短连接：例如普通的web请求，在三次握手之后建立连接，发送数据包并得到服务器返回的结果之后，通过客户端和服务端的四次握手进行关闭断开。

>长连接：区别于短连接，由于三次握手连接及四次握手断开，在请求频繁的情况下，链接请求和断开请求的开销较大，影响效率。采用长连接方式，执行三次握手链接后，不断开链接，保持客户端和服务端通信，直到服务器超时自动断开链接，或者客户端主动断开链接。

>**适用场景：**

>短连接：适用于网页浏览等数据刷新频度较低的场景。

>长连接：适用于客户端和服务端通信频繁的场景，例如聊天室，实时游戏等。

# 24、TCP的粘包、黏包的理解。

# 25、ajax底层原理。