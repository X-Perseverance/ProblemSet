### 1. [一台刚刚接入互联网的 Web 服务器第一次被访问到时，不同协议的发生顺序是下面中的（）](https://www.nowcoder.com/questionTerminal/3f88a6767310418ba791ec321d3a8059)
- [x] A. ARP -> DNS -> HTTP
- [ ] B. ARP -> HTTP -> DNS
- [ ] C. DNS -> HTTP -> ARP
- [ ] D. DNS -> ARP -> HTTP
- [ ] E. HTTP -> ARP -> DNS
- [ ] F. HTTP -> DNS -> ARP

> **【解析】**<br>
> 　　（1）当给 Web 服务器接上网线的时候，它会自动发送一条 ARP 信息，使得接入网关能找到它，网关上会形成一条 Mac 地址到 IP 地址的映射记录；<br>
> 　　（2）当第一个用户使用域名访问 Web 服务器的时候，首先要进行一次 DNS 查询；<br>
> 　　（3）最后才是 HTTP 协议。<br>

### 2. [一台主机要实现通过局域网与另一个局域网通信，需要做的工作是（）](https://www.nowcoder.com/questionTerminal/b8ecc9133e7646a6be0977b63f980b15)
- [ ] A. 配置域名服务器
- [ ] B. 定义一条本机指向所在网络的路由
- [x] C. 定义一条本机指向所在网络网关的路由
- [ ] D. 定义一条本机指向目标网络网关的路由

### 3. [对于 IP 地址为 200.5.6.3 ，属于（）类。](https://www.nowcoder.com/questionTerminal/76488ed1d6e44df094c925c00344499b)
- [ ] A. A
- [ ] B. B
- [x] C. C
- [ ] D. D

### 4. [下列哪些功能使 TCP 准确可靠地从源设备到目地设备传输数据（）](https://www.nowcoder.com/questionTerminal/15e748964cb741fb927544b9bc2d2fff)
- [ ] A. 封装
- [ ] B. 流量控制
- [ ] C. 无连接服务
- [x] D. 编号和定序

### 5. [TCP 三次握手创建连接，双方交互的报文中 SYN 和 ACK 的序列是什么样的（）](https://www.nowcoder.com/questionTerminal/765cc373239544868bb78537aabf51a0)
- [x] A. SYN，SYN+ACK，ACK
- [ ] B. SYN，ACK，SYN，ACK
- [ ] C. SYN+ACK，ACK，SYN
- [ ] D. SYN，SYN，ACK

### 6. [下列关于地址转换的描述，错误的是（）](https://www.nowcoder.com/questionTerminal/11be8925471b4274831067fc95ab4d33)
- [ ] A. 地址转换解决了因特网地址短缺所面临问题
- [x] B. 地址转换实现了对用户透明的网络外部地址的分配
- [ ] C. 使用地址转换后，对“IP包加长”，“快速转发”不会造成什么影响
- [ ] D. 地址转换内部主机提供一定的“隐私”

### 7. [某主机的 IP 地址 202.117.131.12/20 ，其子网掩码是（）](https://www.nowcoder.com/questionTerminal/8e4f0a00ba834e9fa9b9126ebb752ad2)
- [ ] A. 255.255.248.0
- [x] B. 255.255.240.0
- [ ] C. 255.255.252.0
- [ ] D. 255.255.255.4

### 8. [HTTPS 采用（）实现安全网站访问](https://www.nowcoder.com/questionTerminal/a7abf529af4c44c49563d390012c51c8)
- [x] A. SSL
- [ ] B. IPsec
- [ ] C. PGP
- [ ] D. SET

> **【解析】**<br>
> 　　A：SSL（Secure Sockets Layer 安全套接层），是 https 采用的加密通道。<br>
> 　　B：IPSec（InternetProtocolSecurity），用以提供公用和专用网络的端对端加密和验证服务。<br>
> 　　C：PGP（Pretty Good Privacy），是一个基于 RSA 公钥加密体系的邮件加密系统。<br>
> 　　D：SET（安全电子交易协议），是为了在互联网上进行在线交易时，保证信用卡支付的安全而设立的一个开放的规范。<br>

### 9. [某公司申请到一个 C 类地址，但要连接到 6 个子公司，最大的一个子公司有 26 台电脑，每个子公司在一个网段中，则子网掩码应该设成（）](https://www.nowcoder.com/questionTerminal/83cbaa4b476545a49fa4bb6c3020f136)
- [ ] A. 255.255.255.0
- [ ] B. 255.255.255.128
- [ ] C. 255.255.255.192
- [x] D. 255.255.255.224

### 10. [下列关于网络编程错误的是（）](https://www.nowcoder.com/questionTerminal/7f7a4ddd43b3474e863a695869b0677b)
- [ ] A. UDP 是不可靠服务
- [ ] B. 主动关闭的一端会出现 TIME_WAIT 状态
- [ ] C. 服务端编程会调用 listen() ，客户端会调用 bind()
- [x] D. TCP 建立和关闭连接都只需要三次握手
- [ ] E. linux 通过提供 socket 接口来进行网络编程
- [ ] F. 长连接相对短连接可以节省建立连接的时间
