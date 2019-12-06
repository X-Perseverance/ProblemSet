### 1. [IP 地址 205.140.36.68 的哪一部分表示网络号（）](https://www.nowcoder.com/questionTerminal/0108c2d942694aa39c230749b3eb9920)
- [ ] A. 205
- [ ] B. 205.140
- [ ] C. 68
- [x] D. 205.140.36

> **【解析】**<br>
> 　　由于题目中 IP 地址的第一段 205 大于 191 ，所以该地址属于 C 类地址，而 C 类地址的前 24 位表示网络号，后 8 位表示主机号。<br>

### 2. [IP 数据报分片的重组通常发生在（）](https://www.nowcoder.com/questionTerminal/56fa265ca70e41798411ac0f3f220dcd)
- [ ] A. 源主机和数据报经过的路由器上
- [ ] B. 源主机上
- [ ] C. 数据报经过的路由器上
- [x] D. 目的主机上

### 3. [以下不属于 TCP 连接断开的状态是（）](https://www.nowcoder.com/questionTerminal/91aa3ea9c96b4a0399ddb11918ef475e)
- [ ] A. TIME_WAIT
- [ ] B. FIN_WAIT_1
- [x] C. SYNC_SENT
- [ ] D. FIN_WAIT_2

### 4. [IP 地址 10.1.8.0/24 和 10.1.9.0/24 ，下列哪个是正确的汇总网段（）](https://www.nowcoder.com/questionTerminal/0d026c826a99488b8b32e591123bb268)
- [ ] A. 10.0.0.0/8
- [ ] B. 10.1.0.0/16
- [x] C. 10.1.8.0/23
- [ ] D. 10.1.10.0/24

### 5. [属于网络 112.10.200.0/21 的地址是（）](https://www.nowcoder.com/questionTerminal/ba8d33b9806f4993ba5a18473383d8d0)
- [x] A. 112.10.206.0
- [ ] B. 112.10.217.0
- [ ] C. 112.10.224.0
- [ ] D. 112.10.198.0

### 6. [下列 TCP 连接建立过程描述正确的是（）](https://www.nowcoder.com/questionTerminal/6f192d5f529244609d88263c0a230d10)
- [ ] A. 服务端收到客户端的 SYN 包后等待 2*ml 时间后就会进入 SYN_SENT 状态
- [ ] B. 服务端收到客户端的 ACK 包后会进入 SYN_RCVD 状态
- [x] C. 当客户端处于 ESTABLISHED 状态时，服务端可能仍然处于 SYN_RCVD 状态
- [ ] D. 服务端未收到客户端确认包，等待 2*ml 时间后会直接关闭连接

### 7. [TCP 建立连接的过程采用三次握手，已知第三次握手报文的发送序列号为 1000 ，确认序列号为 2000 ，请问第二次握手报文的发送序列号和确认序列号分别为（）](https://www.nowcoder.com/questionTerminal/ddc50f94ab1244f8b23c24fd30dcfc90)
- [ ] A. 1999，999
- [x] B. 1999，1000
- [ ] C. 999，2000
- [ ] D. 999，1999

### 8. [应用程序 PING 发出的是什么报文（）](https://www.nowcoder.com/questionTerminal/0c07913b742749238878702434c70901)
- [ ] A. TCP 请求报文
- [ ] B. TCP 应答报文
- [x] C. ICMP 请求报文
- [ ] D. ICMP 应答报文

### 9. [HTTP 协议中，如果要告知所请求的网页已经永久跳转到了另一个地址，应该返回哪个状态码（）](https://www.nowcoder.com/questionTerminal/e9d3726533e84a1b8b1f3e0407302e78)
- [x] A. 301
- [ ] B. 302
- [ ] C. 404
- [ ] D. 503

### 10. [在因特网中，下列哪个不是 IP 层所需解决的问题（）](https://www.nowcoder.com/questionTerminal/7e327810525842c4bededaf978dcef92)
- [x] A. 流量控制
- [ ] B. 路径选择
- [ ] C. 寻址
- [ ] D. 分段和重新组装
