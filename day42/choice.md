### 1. 下面是一个 http 请求，那么关于 Host、User-Agent、Accept-Charset、Connection、Referer、Cookie 描述错误的是（）
```
<br/>
GET /baidu/blog/item/6605d1b4eb6433738ad4b26d.html HTTP/1.1 <br/>
Host: hi.baidu.com <br/>
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; zh-CN; rv:1.8.0.6) Gecko/20060728 Firefox/1.5.0.6 <br/>
Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5 <br/>
Accept-Language: zh-cn,zh;q=0.5 <br/>
Accept-Encoding: gzip,deflate <br/>
Accept-Charset: gb2312,utf-8;q=0.7,*;q=0.7<br/>
Keep-Alive: 300 <br/>
Connection: keep-alive <br/>
Referer: http://hi.baidu.com/baidu <br/>
Cookie: BAIDUID=AFB70E986AC48B336ABAB7505CDD1C76; <br/>
```

- [ ] A. Host：HTTP服务器的IP地址或者域名
- [ ] B. User-Agent：告诉HTTP服务器，客户端使用的操作系统和浏览器的名称和版本
- [ ] C. Accept-Charset：浏览器申明自己接收的字符集，这就是本文前面介绍的各种字符集和字符编码，如 gb2312，utf-8
- [x] D. Cookie：它记录了服务器的相关的一些信息
- [ ] E. Referer：提供了Request的上下文信息的服务器，告诉服务器我是从哪个链接过来的

### 2. 常见的 http 错误描述原因错误的是（）
- [ ] A. 404-Not Found（没有找到）
- [ ] B. 302-临时重定向
- [ ] C. 500-内部服务器错误
- [x] D. 403-IP address rejected

### 3. linux tcpdump 监听网卡 eth0 ，对方主机 IP 为 10.1.1.180 ，tcp 端口为 80 的数据，相应命令为（）
- [ ] A. tcpdump -h eth0 -nn 'tcp and host 10.1.1.180:80'
- [ ] B. tcpdump -i eth0 -nn 'tcp and host 10.1.1.180:80'
- [ ] C. tcpdump -h eth0 -nn 'tcp and port 80 and host 10.1.1.180'
- [x] D. tcpdump -i eth0 -nn 'tcp and port 80 and host 10.1.1.180'

### 4. 网络地址 172.16.22.38/28 ，请写出此地址的子网 ID 以及广播地址，此地址所处子网可用主机数（）
- [ ] A. 172.16.22.32 172.16.22.255 12
- [ ] B. 172.16.22.32 172.16.22.47 16
- [ ] C. 172.16.22.32 172.16.22.255 15
- [x] D. 172.16.22.32 172.16.22.47 14

### 5. TCP 三次握手的过程，accept 发生在三次握手哪个阶段（）
- [ ] A. 第一次握手
- [ ] B. 第二次握手
- [ ] C. 第三次握手
- [x] D. 三次握手后

### 6. Linux 中，一个端口能够接受 TCP 连接数量的理论上限是（）
- [ ] A. 1024
- [ ] B. 65535
- [ ] C. 65535*65535
- [x] D. 无上限

### 7. TCP 报文首部信息中与关闭连接有关的是（）
- [ ] A. URG
- [ ] B. ACK
- [ ] C. SYN
- [x] D. FIN

### 8. 10.1.0.1/17 的广播地址是（）
- [ ] A. 10.1.128.255
- [ ] B. 10.1.63.255
- [x] C. 10.1.127.255
- [ ] D. 10.1.126.255

### 9. 随着 IP 网络的发展，为了节省可分配的注册 IP 地址，有一些地址被拿出来用于私有 IP 地址，以下不属于私有 IP 地址范围的是（）
- [ ] A. 10.6.207.84
- [ ] B. 172.23.30.28
- [x] C. 172.32.50.80
- [ ] D. 192.168.1.100

### 10. int listen(SOCKET s, int backlog); 该函数中第二个参数的含义是（）
- [ ] A. 是否打开log信息
- [ ] B. 是否打开后台log信息
- [x] C. 后台等待连接队列的最大限制值
- [ ] D. 后台等待连接队列的最小限制值
- [ ] E. 无意义
