### 1. [上网的时候，访问某个网页却突然出现了某个运营商的网页（如联通、电信）。出现此问题可能的原因是（）](https://www.nowcoder.com/questionTerminal/d4a55ebb1348480ca3c90879702c3aaa)
- [x] A. DNS 劫持
- [ ] B. DDoS 攻击
- [ ] C. MAC 地址欺骗
- [ ] D. 伪造 DHCP 服务器

### 2. [TCP 建立连接的三次握手中，第二次握手发送的包会包含的标记，最正确的描述是（）](https://www.nowcoder.com/questionTerminal/8eafa64d32984ae383dc127326ff2a66)
- [ ] A. ACK
- [x] B. SYN, ACK
- [ ] C. SYN, PSH
- [ ] D. SYN

### 3. 当使用 TCP 协议编程时，下列问题哪个是必须由程序员考虑和处理的（）
- [ ] A. 乱序数据包的重传
- [ ] B. 数据传输过程中的纠错
- [ ] C. 网络拥塞处理
- [x] D. 发送数据的格式和应用层协议

### 4. 现在有很多网站都开始选择 HTTPS 作为默认的协议，HTTPS 的用途是（）
- [ ] A. 可以加速页面的加载，提高响应速度
- [ ] B. 可以让服务器端主动推送消息到客户端
- [x] C. 可以确保传输数据的安全性和防篡改
- [ ] D. 为了提高浏览器兼容性

### 5. TCP 断开连接的四次挥手中，第四次挥手发送的包会包含的标记，最正确的描述是（）
- [ ] A. FIN
- [ ] B. FIN, PSH
- [x] C. ACK
- [ ] D. FIN, ACK

### 6. [某浏览器发出的 HTTP 请求报文如下，下列叙述中，错误的是（）](https://www.nowcoder.com/questionTerminal/871cb0951b3b4356a3420630d4057780)
> GET /index.html HTTP/1.1<br>
> Host: www.test.edu.cn<br>
> Connection: Close<br>
> Cookie: 123456<br>
- [ ] A. 该浏览器请求浏览 index.html
- [ ] B. index.html 存放在 www.test.edu.cn 上
- [x] C. 该浏览器请求使用持续连接
- [ ] D. 该浏览器曾经浏览过 www.test.edu.cn

> **【解析】**<br>
> 　　`Connection`: Close 表示**非持续连接**方式，keep-alive 表示**持续连接**方式。<br>
> 　　`Cookie`: 由服务器产生，在 HTTP 请求报文中有 Cookie 表示曾经访问过 www.test.edu.cn 服务器。<br>

### 7. [主机甲和主机乙新建一个 TCP 连接，甲的拥塞控制初始阈值为 32KB ，甲向乙始终以 MSS=1KB 大小的段发送数据，并一直有数据发送；乙为该连接分配 16KB 接收缓存，并对每个数据段进行确认，忽略段传输延迟。若乙收到的数据全部存入缓存，不被取走，则甲从连接建立成功时刻起，未发送超时的情况下，经过 4 个 RTT 后，甲的发送窗口是（）](https://www.nowcoder.com/questionTerminal/3241441c88f04ab58585a187716055d3)
- [x] A. 1KB
- [ ] B. 8KB
- [ ] C. 16KB
- [ ] D. 32KB

> **【解析】**

| | 通知窗口大小，代表接收缓存剩余值 | 拥塞窗口大小| 发送窗口大小 |
|:--:|:--:|:--:|:--:|
| 初始值 | 16 | 1 | 1 |
| 经过第一个RTT | 16-1=15 | 2 | min(15,2)=2 |
| 经过第二个RTT | 15-2=13 | 4 | min(13,4)=4 |
| 经过第三个RTT | 13-4=9 | 8 | min(9,8)=8 |
| 经过第四个RTT | 9-8=1 | 16 | min(16,1)=1 |

### 8. [通过 POP3 协议接收邮件时，使用的传输层服务类型是（）](https://www.nowcoder.com/questionTerminal/26625c7d394441438621b77619c18f1e)
- [ ] A. 无连接不可靠的数据传输服务
- [ ] B. 无连接可靠的数据传输服务
- [ ] C. 有连接不可靠的数据传输服务
- [x] D. 有连接可靠的数据传输服务

### 9. [下列关于 UDP 协议的叙述中，正确的是（）](https://www.nowcoder.com/questionTerminal/443cfef7c2504b6db5804732ebaad650)
> Ⅰ 提供无连接服务<br>
> Ⅱ 提供复用/分用服务<br>
> Ⅲ 通过差错校验，保障可靠数据传输<br>
- [ ] A. 仅Ⅰ
- [x] B. 仅Ⅰ、Ⅱ
- [ ] C. 仅Ⅱ、Ⅲ
- [ ] D. Ⅰ、Ⅱ、Ⅲ

### 10. [主机甲与主机乙之间已建立一个 TCP 连接，双方持续有数据传输，且数据无差错与丢失。若甲收到 1 个来自乙的 TCP 段，该段的序号为 1913 ，确认序号为 2046 ，有效载荷为 100 字节，则甲立即发送给乙的 TCP 段的序号和确认序号分别是（）](https://www.nowcoder.com/questionTerminal/d451cb19634640128363c24a432e47e2)
- [ ] A. 2046、2012
- [x] B. 2046、2013
- [ ] C. 2047、2012
- [ ] D. 2047、2013

> **【解析】**<br>
> 　　（1）甲收到的段序号为 1913 ，说明乙发给甲的数据段起始序号为 1913 ，又因为有效载荷为 100 字节，说明数据段长度为 100 ，那么甲这次收到的数据就是 1913~2012 这段，下次需要的数据就是从 2013 开始，所以**甲发送给乙的确认序号**就是 2013 。<br>
> 　　（2）甲收到的确认序号为 2046 ，说明乙这次需要的数据段是以 2046 作为起始序号的，所以**甲发送给乙的段序号**为 2046。<br>