### 1. [若一个用户进程通过 read 系统调用读取一个磁盘文件中的数据，则下列关于此过程的叙述中，正确的是（）](https://www.nowcoder.com/questionTerminal/59acb0da2ea54842b794bb7d2fc89d9a)
Ⅰ. 若该文件的数据不在内存中，则该进程进入睡眠等待状态<br>
Ⅱ. 请求 read 系统调用会导致 CPU 从用户态切换到核心态<br>
Ⅲ. read 系统调用的参数应包含文件的名称<br>
- [x] A. 仅Ⅰ、Ⅱ
- [ ] B. 仅Ⅰ、Ⅲ
- [ ] C. 仅Ⅱ、Ⅲ
- [ ] D. Ⅰ、Ⅱ和Ⅲ

### 2. [下列关于虚拟存储的叙述中，正确的是（）](https://www.nowcoder.com/questionTerminal/ac4f123ef6d344c2817158d83277032a)
- [ ] A. 虚拟存储只能基于连续分配技术
- [x] B. 虚拟存储只能基于非连续分配技术
- [ ] C. 虚拟存储容量只受外存容量的限制
- [ ] D. 虚拟存储容量只受内存容量的限制

### 3. [下列选项中，不可能在用户态发生的事件是（）](https://www.nowcoder.com/questionTerminal/3d628c9a60ac4b5daa11efc40d7b8868)
- [ ] A. 系统调用
- [ ] B. 外部中断
- [x] C. 进程切换
- [ ] D. 缺页

### 4. [在虚拟内存管理中，地址变换机构将逻辑地址变为物理地址，形成该逻辑地址的阶段是（）](https://www.nowcoder.com/questionTerminal/148e1e7ebc694081bbb61dfdb92e9af2)
- [ ] A. 编辑
- [ ] B. 编译
- [x] C. 链接
- [ ] D. 装载

### 5. [在缺页处理过程中，操作系统执行的操作可能是（）](https://www.nowcoder.com/questionTerminal/645b2b82da724b619d0671ea9c72b94b)
Ⅰ.修改页表　Ⅱ.磁盘 I/O　Ⅲ.分配页框<br>
- [ ] A. 仅Ⅰ、 Ⅱ
- [ ] B. 仅Ⅱ
- [ ] C. 仅Ⅲ
- [x] D. Ⅰ、Ⅱ和Ⅲ

### 6. [下面选项中，满足短任务优先且不会发生饥饿现象的调度算法是（）](https://www.nowcoder.com/questionTerminal/82f9ee8a78524941a475c58ca22552bd)
- [ ] A. 先来先服务
- [x] B. 高响应比优先
- [ ] C. 时间片轮转
- [ ] D. 非抢占式短任务优先

### 7. [下列选项中，降低进程优先级的合理时机是（）](https://www.nowcoder.com/questionTerminal/b7fc3206a6154b6eb45862f4eafa0479)
- [x] A. 进程的时间片用完
- [ ] B. 进程刚完成I/O，进入就绪列队
- [ ] C. 进程持久处于就绪列队
- [ ] D. 进程从就绪状态转为运行态

### 8. [在使用锁保证线程安全时，可能会出现活跃度失败的情况，活跃度失败主要包括（）](https://www.nowcoder.com/questionTerminal/dd4047e246b449f099c5319c658b69d8)
- [ ] A. 死锁
- [ ] B. 饥饿
- [ ] C. 活锁
- [x] D. 以上全部

### 9. [下列选项中，导致创建新进程的操作是（）](https://www.nowcoder.com/questionTerminal/d014af090bd14350b7f09f0f8e487555)
I.用户登陆成功　II.设备分配　III.启动程序执行<br>
- [ ] A. 仅I和II
- [ ] B. 仅II和III
- [x] C. 仅I和III 
- [ ] D. I、II和III

### 10. [对进程和线程的描述，以下正确的是（）](https://www.nowcoder.com/questionTerminal/c12a7100138a4a38ab9dfa9f1d85743f)
- [ ] A. 父进程里的所有线程共享相同的地址空间，父进程的所有子进程共享相同的地址空间
- [ ] B. 改变进程里面主线程的状态会影响到其他线程的行为，改变父进程的状态不会影响到其他子进程
- [ ] C. 多线程会引起死锁，而多进程不会
- [x] D. 以上选项都不正确
