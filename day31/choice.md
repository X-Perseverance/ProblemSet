### 1. [在 OSI 分层模型中，把传输的比特流划分为帧，是哪一层的功能（）](https://www.nowcoder.com/questionTerminal/e42707b6168244468b45dc4ed103e582)
- [ ] A. 物理层
- [ ] B. 网络层
- [x] C. 数据链路层
- [ ] D. 传输层

> 【解析】<br>
> 　　传输层 —— 段<br>
> 　　网络层 —— 包<br>
> 　　数据链路层 —— 帧<br>
> 　　物理层 —— 比特流<br>

### 2. [下面关于源端口地址和目标端口地址的描述中，正确的是（）](https://www.nowcoder.com/questionTerminal/8e601d33390145bfbe1417f9178e01e5)
- [x] A. 在 TCP/UDP 传输段中，源端口地址和目的端口地址是不能相同的
- [ ] B. 在 TCP/UDP 传输段中，源端口地址和目的端口地址必须是相同的
- [ ] C. 在 TCP/UDP 传输段中，源端口地址和目的端口地址是可以相同的
- [ ] D. 以上描述均不正确

### 3. [网段地址 154.27.0.0 的网络，若不做子网划分，能支持（）台主机](https://www.nowcoder.com/questionTerminal/2796316c9450442c864daef0ec4b3eba)
- [ ] A. 254
- [ ] B. 1024
- [x] C. 65,534
- [ ] D. 16,777,206

> 【解析】<br>
> 　　`154.27.0.0` 为 B 类地址，后16位为主机号，可提供的主机号个数为 2^16 个，除去全0和全1号码，可以支持`65534`台主机。<br>

### 4. [SNMP 使用 udp 161 和 162 端口，则该协议属于 TCP/IP 模型中的（）](https://www.nowcoder.com/questionTerminal/f8365cdd6af04787ac3f162760a93bb3)
- [ ] A. 网络层
- [ ] B. 数据链路层
- [x] C. 应用层
- [ ] D. 传输层

> 【解析】<br>
> 　　简单网络管理协议（SNMP）是专门设计用于在 IP 网络管理网络节点（服务器、工作站、路由器、交换机及HUBS等）的一种标准协议，它是一种应用层协议。<br>

### 5. http 协议中，状态码 500 的意思为（）
- [ ] A. 重定向
- [ ] B. 访问被拒绝
- [ ] C. 未找到请求的内容
- [x] D. 服务器内部有错误

### 6. [主机 A 向主机 B 连续发送了两个 TCP 报文段，其序号分包是 70 和 100 ，如果 A 发送的第一个报文段丢失了，但第二个报文段达到了 B ，B 在第二个报文段到达后向 A 发送确认，那么这个确认号是多少（）](https://www.nowcoder.com/questionTerminal/3c0fbfcd546d44a59506494e311b2719)
- [ ] A. 100
- [ ] B. 101
- [x] C. 70
- [ ] D. 71

### 7. [每个 IP 地址都可以有一个主机名，通过主机名得到该主机对应 IP 地址的过程叫（）](https://www.nowcoder.com/questionTerminal/387ebdd0389e4d33ad57a9d657df77ec)
- [ ] A. IP 地址解析
- [x] B. 域名解析
- [ ] C. 域名编译
- [ ] D. IP 地址编译

### 8. [以下说法不正确的是（）](https://www.nowcoder.com/questionTerminal/32321491d45b4d1eb28e4ee350af49be)
- [ ] A. HTTP 是一种请求/响应式的协议
- [ ] B. HTTP 请求消息中 Accept 表示浏览器可接受的 MIME 类型
- [ ] C. HTTP 请求消息中 Accept-Encoding 表示浏览器能够进行解码的数据编码方式
- [x] D. HTTP 请求消息中 Css 表示初始 URL 中的主机和端口

> 【解析】<br>
> 　　HTTP 请求消息中 Host 表示初始 URL 中的主机和端口。<br>

### 9. [关于计算机网络，下列描述当中，正确的是（）](https://www.nowcoder.com/questionTerminal/306ec4ccf4ee44f5847e9370dd41dc87)
- [ ] A. 在同一信道上同一时刻，可进行双向数据传送的通信方式是半双工
- [ ] B. TCP 协议是无连接的；UDP 协议是面向连接的
- [x] C. 假设一个主机的 IP 地址为 192.168.8.123 ，而子网掩码为 255.255.255.248 ，那么该主机的网络号是 192.168.8.120
- [ ] D. 计算机网络中的 OSI 结构分别是：物理层，数据链路层，传输层，会话层，表示层，应用层

> 【解析】<br>
> 　　A：在同一信道上同一时刻，可进行双向数据传送的通信方式是全双工；<br>
> 　　B：TCP 协议是有连接的，而 UDP 协议是无连接的；<br>
> 　　C：将 IP 地址和子网掩码相与便可得到网络号；<br>
> 　　D：OSI 结构一共有七层，还包括网络层。<br>

### 10. [下列关于 HTTP 状态码描述正确的是（）](https://www.nowcoder.com/questionTerminal/e254925dc876405eafc85cfc91111230)
- [ ] A. 404 读取浏览器缓存，502 错误网关
- [ ] B. 404 找不到资源，403 服务器错误
- [x] C. 500 服务器错误，304 读取浏览器缓存
- [ ] D. 304 服务器错误，200 请求成功
- [ ] E. 500 找不到资源，200 请求成功
