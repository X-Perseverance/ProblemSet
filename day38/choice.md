### 1. [IPv4 版本的因特网总共有多少有效 A 类地址网络（）](https://www.nowcoder.com/questionTerminal/b314cee1648b4699a20f4e10fec483f6)
- [ ] A. 255
- [ ] B. 128
- [ ] C. 256
- [x] D. 126

> **【解析】**<br>
> 　　A 类网络的网络地址部分占 8 位，其中第一位为 0 ，再除去保留的全 0 和全 1 ，所以有效的网络地址有 `2^7-2=126` 个。<br>

### 2. [一条 TCP 连接，主动关闭的一方不可能出现的连接状态是（）](https://www.nowcoder.com/questionTerminal/0d07822c751c41ff865401d77c17364d)
- [x] A. CLOSE_WAIT
- [ ] B. FIN_WAIT2
- [ ] C. TIME_WAIT
- [ ] D. FIN_WAIT1

### 3. [下列有关 Socket 的说法，错误的是（）](https://www.nowcoder.com/questionTerminal/e21bb3bd49954a5eb87ea56a9d0bc6c2)
- [ ] A. Socket 用于描述 IP 地址和端口，是一个通信链的句柄
- [x] B. Socket 通信必须建立连接
- [ ] C. Socket 客户端的端口是不固定的
- [ ] D. Socket 服务端的端口是固定的

> **【解析】**<br>
> 　　选项B：Socket 通信可以基于 TCP ，也可以基于 UDP ，前者是面向连接的，而后者是面向无连接的。<br>

### 4. [关于 ARP 表，以下描述中正确的是（）](https://www.nowcoder.com/questionTerminal/d7866231d0b64c97b979bedde527835a)
- [ ] A. 用于在各个子网之间进行路由选择
- [ ] B. 提供常用目标地址的快捷方式来减少网络流量
- [x] C. 用于建立 IP 地址到 MAC 地址的映射
- [ ] D. 用于进行应用层信息的转换

### 5. [下面对于 cookie 的描述中错误的是（）](https://www.nowcoder.com/questionTerminal/3f2c6e6e1b83413a8ba54616166bbf36)
- [ ] A. 如果在一台计算机中安装多个浏览器，每个浏览器都会以独立的空间存放 cookie
- [ ] B. cookie 的大小限制在 4kb 左右，对于复杂的存储需求来说是不够用的
- [x] C. cookie 通过 HTTP Headers 从浏览器端发送到服务器端并存储在服务器端
- [ ] D. 由于在 HTTP 请求中的 cookie 是明文传递的，所以安全性成问题

> **【解析】**<br>
> 　　cookie 存储在客户端。<br>

### 6. [攻击者采用某种手段，使用户访问某网站时获得一个其他网站的 IP 地址，从而将用户的访问引导到其他网站，这种攻击手段称为（）](https://www.nowcoder.com/questionTerminal/fb59d9aa03aa4ce0a073c858ab27dd6e)
- [ ] A. ARP 欺骗攻击
- [ ] B. 重放攻击
- [ ] C. 暴力攻击
- [x] D. DNS 欺骗攻击

### 7. [IP 地址中的哪个类默认有最多可用的主机地址（）](https://www.nowcoder.com/questionTerminal/a81d292021654f6e89bacb53f2b499bf)
- [x] A. A
- [ ] B. B
- [ ] C. C
- [ ] D. A和B

### 8. [下面哪个协议被用来找到本地设备的硬件地址（）](https://www.nowcoder.com/questionTerminal/9e0d6d18ed5b432bb9565d12231b4434)
- [ ] A. RARP
- [x] B. ARP
- [ ] C. IP
- [ ] D. IMCP

### 9. [在以下协议中，那个协议与其他协议是不属于同一类的（）](https://www.nowcoder.com/questionTerminal/2dd17785c1e044f9949b6f3fb7d0428c)
- [ ] A. FTP
- [x] B. ICMP
- [ ] C. TELNET
- [ ] D. SMTP
- [ ] E. DNS

> **【解析】**<br>
> 　　ICMP 属于网络层协议，其它都属于应用层协议。<br>

### 10. [在网络应用测试中，网络延迟是一个重要指标。以下关于网络延迟的理解，正确的是（）](https://www.nowcoder.com/questionTerminal/667fdef01afb429db3216105000f2bba)
- [ ] A. 指响应时间
- [ ] B. 指报文从客户端发出到客户端接收到服务器响应的间隔时间
- [ ] C. 指报文在网络上的传输时间
- [x] D. 指从报文开始进入网络到它开始离开网络之间的时间
