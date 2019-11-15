### 1. [/etc/resolv.conf 的用途是（）](https://www.nowcoder.com/questionTerminal/91ca0f351f6549e4a560bc2b4a8350f9)
- [ ] A. 邮件服务的设置文件
- [ ] B. DHCP 的设置文件
- [x] C. DNS 解析的设置文件
- [ ] D. 网络路由的设置文件

> **【解析】**<br>
> 　　DNS 解析的设置文件在：`/etc/resolv.conf`<br>
> 　　邮件服务的设置文件：`/etc/mail.rc`<br>
> 　　DHCP 的设置文件：`/etc/dhcpd.conf`<br>
> 　　网络路由的设置文件：`/etc/gateways`<br>

### 2. [能够 ping 通同网段的节点，但却 ping 不通其他网段的所有节点的最可能原因是（）](https://www.nowcoder.com/questionTerminal/004d52649de4471896683e7aa33e0891)
- [x] A. 本机网关设置错误
- [ ] B. 本机没有正确设置 DNS
- [ ] C. 对方运行的是不同的操作系统
- [ ] D. 二层交换机故障

> **【解析】**<br>
> 　　A 正确，ping 是 TCP/IP 协议族的一部分，其属于网络层协议，主要是用来检测网络是否通畅，如果要 ping 其他网段则需要设置网关。<br>
> 　　B 错误，和 DNS 没关系，DNS 设置错会影响访问公网服务器的域名，而不会影响内部子设备直接是否 ping 通。<br>
> 　　C 错误，ping 命令是跨操作系统的，即 Windows 主机能 ping 通 Linux 主机。<br>
> 　　D 错误，二层交换机如果出现故障那么同网段主机则不会 ping 通。<br>

### 3. [常被提及的 DoS 攻击是以下哪个行为（）](https://www.nowcoder.com/questionTerminal/9855892ed9224c068dabf02a5f5f55f6)
- [ ] A. 侵入目标服务器，获取重要数据
- [ ] B. 采用穷举的方式获得登录账号
- [x] C. 发送无效的请求，使得正确的请求无法被响应
- [ ] D. 利用微软 DOS 从操作系统图的各种漏洞达到攻击的目的

> **【解析】**<br>
> 　　[DoS 攻击介绍](https://baike.baidu.com/item/dos%E6%94%BB%E5%87%BB)<br>

### 4. [以下不是 DNS 服务的作用的是（）](https://www.nowcoder.com/questionTerminal/120b9663b7804b5fbb337d4ac3a40cc3)
- [ ] A. 将主机名翻译到指定的 IP 地址
- [ ] B. 将 IP 地址反解成主机名
- [ ] C. 解析特定类型的服务的地址，如MX、NS
- [x] D. 将 IP 解析成 MAC 地址

> **【解析】**<br>
> 　　DNS（域名系统），将域名转换为 IP 地址，也可以将 IP 地址转换为相应的域名地址。<br>
> 　　ARP（地址解析协议），通过 IP 地址获取物理地址。<br>

### 5. [在小红书公司的局域网中，署队长的私人电脑可以查看到同事的电脑，也成功了登录了QQ，但却无法访问到公司的站点 http://www.xiaohongshu.com ，请协助署队长查找最有可能出现问题的地方是（）](https://www.nowcoder.com/questionTerminal/11be1db1e87648e5b22e0d4edfe4353c)
- [ ] A. UDP
- [ ] B. DHCP
- [x] C. DNS
- [ ] D. HTTP
- [ ] E. 浏览器

### 6. [将一个 C 类网络划分 20 个子网，最适合的子网掩码是多少（）](https://www.nowcoder.com/questionTerminal/aae2457a009a4a55964c66fe5785d6f4)
- [ ] A. 255.255.255.240
- [x] B. 255.255.255.248
- [ ] C. 255.255.255.252
- [ ] D. 255.255.255.255

> **【解析】**<br>
> 　　对于 C 类网络来说，前 24 位为网络号，后 8 位为主机号，而**划分子网的方法是从网络的主机号中借用若干位来作为子网号**。对该题而言，若要划分 20 个子网，那么就需要从主机号中至少借用 5 位作为子网号才能满足所需子网数，因为`2^4 < 20 < 2^5`，所以最终的子网掩码就是：`11111111 11111111 11111111 11111000`，即：`255.255.255.248`。<br>

### 7. [以下哪种 HTTP 状态下，浏览器会产生两次 HTTP 请求（）](https://www.nowcoder.com/questionTerminal/944a0682fda24b1881d0a0c687054573)
- [ ] A. 400
- [ ] B. 404
- [x] C. 302
- [ ] D. 304

### 8. [局域网的网络地址 192.168.1.0/24 ，局域网络连接其他网络的网关地址是 192.168.1.1 。主机 192.168.1.20 访问 172.16.1.0/24 网络时，其路由设置正确的是（）](https://www.nowcoder.com/questionTerminal/9328384a3b2948aeb4d25f3d871ae8c5)
- [ ] A. route add default 192.168.1.0 netmask 172.16.1.1 metric 1
- [x] B. route add -net 172.16.1.0 gw 192.168.1.1 netmask 255.255.255.0 metric 1
- [ ] C. route add -net 192.168.1.0 gw 192.168.1.1 netmask 255.255.255.0 metric 1
- [ ] D. route add -net 172.16.1.0 gw 172.16.1.1 netmask 255.255.255.0 metric 1

### 9. [建立一条 TCP 连接需要（）个步骤，关闭一个 TCP 连接需要（）个步骤。](https://www.nowcoder.com/questionTerminal/73663347b0c84df987e5b6a06cfdfbf4)
- [ ] A. 4，3
- [ ] B. 4，4
- [x] C. 3，4
- [ ] D. 3，3

### 10. [以下关于 HTTP 状态码的描述，错误的是（）](https://www.nowcoder.com/questionTerminal/c6a59e94fcaa4e97bba95e3be50441c3)
- [ ] A. 100，代表客户端应当继续发送请求
- [ ] B. 2xx，代表请求已成功被服务器接收、理解、并接受
- [ ] C. 301，代表被请求的资源已永久移动到新位置，用于重定向
- [x] D. 4xx，代表服务器在处理请求的过程中有错误或者异常状态发生
