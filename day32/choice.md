### 1. [在计算机网络中， TCP 和 UDP 协议的相似之处是（）](https://www.nowcoder.com/questionTerminal/8cca7ded1d294669b833d71bd1297541)
- [ ] A. 面向非连接的协议
- [ ] B. 面向连接的协议
- [ ] C. 其余选项都不对
- [x] D. 传输层协议

### 2. [在 OSI 参考模型中能实现路由选择，拥塞控制与互联功能的层是（）](https://www.nowcoder.com/questionTerminal/1ded69a625b04399815ec23989ef4666)
- [ ] A. 物理层
- [x] B. 网络层
- [ ] C. 数据链路层
- [ ] D. 应用层

### 3. [在 TCP/IP 中， ICMP 属于哪一层协议（）](https://www.nowcoder.com/questionTerminal/21823f2f18ae4465b2e56181649e5ef9)
- [x] A. IP
- [ ] B. PPP
- [ ] C. UDP
- [ ] D. TCP

> 【解析】<br>
> 　　ICMP（Internet Control Message Protocol），即**Internet控制报文协议**，它是TCP/IP协议簇的一个子协议，用于在IP主机、路由器之间传递控制消息。控制消息是指网络通不通、主机是否可达、路由是否可用等网络本身的消息。这些控制消息虽然并不传输用户数据，但是对于用户数据的传递起着重要的作用。<br>

### 4. [在发送 TCP 接收到确认 ACK 之前，由其设置的重传计时器到时，这时发送 TCP 会（）](https://www.nowcoder.com/questionTerminal/28e69cbfb2464e90a3d4d12828e66bf6)
- [x] A. 重传重要的数据段
- [ ] B. 放弃该连接
- [ ] C. 调整传送窗口尺寸
- [ ] D. 向另一个目标端口重传数据

### 5. [下列哪项最恰当地描述了建立 TCP 连接时“第一次握手”所做的工作（）](https://www.nowcoder.com/questionTerminal/344b93dbb88b457b8f67a2bef0b48ab8)
- [ ] A. “连接发起方”向“接收方”发送一个 SYN-ACK 段
- [ ] B. “接收方”向“连接发起方”发送一个 SYN-ACK 段
- [x] C. “连接发起方”向目标主机的 TCP 进程发送一个 SYN 段
- [ ] D. “接收方”向源主机得到 TCP 进程发送一个 SYN 段作为应答

### 6. [关于以下 URL 的描述错误的是（）](https://www.nowcoder.com/questionTerminal/f8d956fd033e459f91d7bde6d51c19c9)
- [x] A. http 表明使用 TCP 协议
- [ ] B. 又名统一资源定位符，方便确定一个资源，并表示它在哪里
- [ ] C. URL 中隐藏了端口号，默认是 80 端口
- [ ] D. 访问 URL 可使用大写字母

### 7. [不属于交换机攻击的是（）](https://www.nowcoder.com/questionTerminal/d441bf97ae644449a54be04f67b2819d)
- [x] A. 目录遍历攻击
- [ ] B. MAC 泛洪攻击
- [ ] C. VLAN 攻击
- [ ] D. DHCP 欺骗攻击

### 8. [在下面给出的协议中，（）是 TCP/IP 的应用层协议。](https://www.nowcoder.com/questionTerminal/08b4cbadf09344d0830904f40be5e335)
- [ ] A. ARP 和 FTP
- [x] B. DNS 和 SMTP
- [ ] C. RARP 和 DNS
- [ ] D. ICMP 和 IGMP

> 【解析】<br>
> 　　`ARP`：网络层-数据链路层<br>
> 　　`FTP`：应用层<br>
> 　　`DNS`：应用层<br>
> 　　`SMTP`：应用层<br>
> 　　`RARP`：网络层-数据链路层<br>
> 　　`ICMP`：网络层<br>
> 　　`IGMP`：网络层<br>

### 9. [IP地址块为 211.168.15.192/26 、 211.168.15.160/27 和 211.168.15.128/27 三个地址块经聚合后可用地址数为（）](https://www.nowcoder.com/questionTerminal/d67169b5b11a47c58679b5c446233924)
- [x] A. 126
- [ ] B. 62
- [ ] C. 128
- [ ] D. 68

> 【解析】<br>
> 　　`211.168.15.192/26` -> `211.168.15.11000000`<br>
> 　　`211.168.15.160/27` -> `211.168.15.10100000`<br>
> 　　`211.168.15.128/27` -> `211.168.15.10000000`<br>
> 　　由此，可得出聚合后的地址块为`211.168.15.10000000`，即`211.168.15.128/25`，所以可用地址数为：`2^(32-25)-2=126`。<br>

### 10. [以下不是合法 HTTP 请求方法的是（）](https://www.nowcoder.com/questionTerminal/b6c9cb15c9ee455295bbc7e9f13581db)
- [ ] A. GET
- [x] B. SET
- [ ] C. HEAD
- [ ] D. PUT
