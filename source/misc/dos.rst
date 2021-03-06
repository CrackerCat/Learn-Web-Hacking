拒绝服务攻击
================================

简介
--------------------------------
DoS（Denial of Service）指拒绝服务，是一种常用来使服务器或网络瘫痪的网络攻击手段。

在平时更多提到的是分布式拒绝服务（DDoS，Distributed Denial of Service） 攻击，该攻击是指利用足够数量的傀儡计算机产生数量巨大的攻击数据包，对网络上的一台或多台目标实施DoS攻击，从而耗尽受害目标的资源，迫使目标失去提供正常服务的能力。

UDP反射
--------------------------------
基于UDP文的反射DDoS攻击是拒绝服务攻击的一种形式。攻击者不直接攻击目标，而是利用互联网中某些开放的服务器，伪造被攻击者的地址并向该服务器发送基于UDP服务的特殊请求报文，使得数倍于请求报文的数据被发送到被攻击IP，从而对后者间接形成DDoS攻击。

常用于DoS攻击的服务有:

- NTP
- SSDP
- Memcached

TCP Flood
--------------------------------
TCP Flood是一种利用TCP协议缺陷的攻击，这种方式通过伪造IP向攻击服务器发送大量伪造的TCP SYN请求，被攻击服务器回应握手包后（SYN+ACK），因为伪造的IP不会回应之后的握手包，服务器会保持在SYN_RECV状态，并尝试重试。这会使得TCP等待连接队列资源耗尽，正常业务无法进行。

Shrew DDoS
--------------------------------
Shrew DDoS利用了TCP的重传机制，调整攻击周期来反复触发TCP协议的RTO，达到攻击的效果。其数据包以固定的、恶意选择的慢速时间发送，这种模式能够将TCP流量限制为其理想速率的一小部分，同时以足够低的平均速率进行传输以避免检测。

现代操作系统已经对TCP协议进行了相应的修改，使得其不受影响。


Ping Of Death
--------------------------------
在正常情况下不会存在大于65536个字节的ICMP包，但是报文支持分片重组机制。通过这种方式可以发送大于65536字节的ICMP包并在目标主机上重组，最终会导致被攻击目标缓冲区溢出，引起拒绝服务攻击。

现代操作系统已经对这种攻击方式进行检查，使得其不受影响。

Challenge Collapsar (CC)
--------------------------------
CC攻击是一种针对资源的DDoS攻击，攻击者通常会常用请求较为消耗服务器资源的方式来达到目的。常见的攻击通过搜索页，物品展示页来实现。

参考链接
--------------------------------
- `linux academy dos <https://linuxacademy.com/howtoguides/posts/show/topic/13191-denial-of-service-dos>`_
