### 1. [X86 体系结构在保护模式下中有三种地址，请问一下那种说法是正确的？（）](https://www.nowcoder.com/questionTerminal/f20853c7594e460e91f91c196047e94d)
- [x] A. 虚拟地址先经过分段机制映射到线性地址，然后线性地址通过分页机制映射到物理地址
- [ ] B. 线性地址先经过分段机制映射到虚拟地址，然后虚拟地址通过分页机制映射到物理地址
- [ ] C. 虚拟地址先经过分页机制映射到线性地址，然后线性地址通过分段机制映射到物理地址
- [ ] D. 线性地址先经过分页机制映射到虚拟地址，然后虚拟地址通过分段机制映射到物理地址

### 2. [对于 Linux 说法，下列说法正确的是（）](https://www.nowcoder.com/questionTerminal/d0bfbb3bdd3647b79e7a52c9b5fa1983)
- [x] A. 线性访问内存非法时，当前线程会进入信号处理函数
- [ ] B. 用 mv 命令移动文件时，文件的修改时间会发生变化
- [ ] C. ulimit -c 设置的是函数调用栈的大小
- [ ] D. malloc 函数是应用程序向操作系统申请内存的接口

### 3. [以下说法不正确的是（）](https://www.nowcoder.com/questionTerminal/81435d54c5a84ba78eb2c3114f82370f)
- [x] A. 进程调度中“可抢占”和“非抢占”两种方式，后者引起系统的开销更大
- [ ] B. 每个进程都有自己的文件描述符表，所有进程共享同一打开文件表和 v-node 表
- [ ] C. 基本的存储技术包括 RAM ， ROM ，磁盘以及 SSD ，其中访问速度最慢的是磁盘， CPU 的高速缓存一般是由 RAM 组成的
- [ ] D. 多个进程竞争源出现了循环等待可能造成系统死锁

### 4. [单任务系统中两个程序 A 和 B ，若执行顺序为 A->B ，那么 CPU 的利用率是（）](https://www.nowcoder.com/questionTerminal/17761a771a714f8aa26027e79c801174)
A程序：CPU:10s -> 设备1:5s -> CPU:5s -> 设备2:10s -> CPU:10s；<br>
B程序：设备1:10s -> CPU:10s -> 设备2:5s -> CPU:5s -> 设备2:10s；<br>
- [ ] A. 30%
- [ ] B. 40%
- [x] C. 50%
- [ ] D. 60%

> 【解析】<br>
> 　　从题目中的关键词**单任务系统**来看，A、B两个程序只能顺序执行，而不能并发执行，所以我们只需要计算出**CPU花费的时间**以及**程序总共花费的时间**，两者相除便是问题的答案。<br>
> 　　**A程序**：CPU花费的时间=10+5+10=25s，总共花费的时间=10+5+5+10+10=40s<br>
> 　　**B程序**：CPU花费的时间=10+5=15s，总共花费的时间=10+10+5+5+10=40s<br>
> 　　**CPU的利用率**：`(25+15)/(40+40)=50%`<br>

### 5. [下述哪种情况会提出中断请求（）](https://www.nowcoder.com/questionTerminal/f7d713f3934c4ea3ba6d30b2a99aedf7)
- [x] A. 在键盘输入过程中，每按一次键
- [ ] B. 两数相加结果为零
- [ ] C. 计算结果溢出
- [ ] D. 一条系统汇编指令执行完成

### 6. [以下哪些不是内核对象（）](https://www.nowcoder.com/questionTerminal/4eb5b077621d48858cfaf47d644d9655)
- [ ] A. 进程
- [ ] B. 线程
- [ ] C. 互斥器
- [x] D. 临界区

### 7. [如果系统的 umask 设置为 244 ，创建一个新文件后，它的权限为（）](https://www.nowcoder.com/questionTerminal/d26a5b36d4e546bf8396c41c6b5f81ab)
- [ ] A. --w-r--r--
- [ ] B. -r-xr--r--
- [x] C. -r---w--w-
- [ ] D. -r-x-wx-wx

> 【解析】<br>
> 　　`umask` 的功能是指定在建立文件时预设的权限掩码，对于一个新建的文件，其权限为该文件的默认权限和权限掩码之差，而文件的默认权限是666，目录的默认权限是777，所以对本道题来说，新建文件的权限 = 666-244 = 422，即选项C。<br>

### 8. [由源代码生成可执行文件需要经过预编译，编译，汇编，链接等阶段，错误：unresolved external symbol BeginScene 属于（）阶段错误。](https://www.nowcoder.com/questionTerminal/b491ad824f404c28a3d1847f533af4c3)
- [ ] A. 预编译
- [ ] B. 编译
- [ ] C. 汇编
- [x] D. 链接

### 9. [程序出错在什么阶段（）](https://www.nowcoder.com/questionTerminal/fe79e94bed4e43dc89f03d7df368a5d6)
```c
int main(void)
{
	http://www.taobao.com
	cout << "welcome to taobao" << endl;
	return 0;
}
```
- [ ] A. 预处理阶段出错
- [ ] B. 编译阶段出错
- [ ] C. 汇编阶段出错
- [ ] D. 链接阶段出错
- [ ] E. 运行阶段出错
- [x] F. 程序运行正常

> 【解析】<br>
>　　 `http`相当于一个**标签**，`//www.taobao.com`是一个**注释**，所以程序正常运行。<br>

### 10. [有一个变量 int a=0; 两个线程同时进行 +1 操作，每个线程加 100 次，不加锁，最后 a 的值是（）。](https://www.nowcoder.com/questionTerminal/391a35abea3f433c82ca97e554496d0c)
- [ ] A. 200
- [x] B. <=200
- [ ] C. >=200
- [ ] D. 都有可能

> 【解析】<br>
>　　单核CPU：最小值100，最大值200<br>
>　　多核CPU：最小值2，最大值200<br>
