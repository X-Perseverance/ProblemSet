### 1. [下面的程序执行输出几个hello？（）](https://www.nowcoder.com/questionTerminal/6432b302f7ca41db963e1adbba6287c1)
```c
#include <stdio.h>
#include <unistd.h>

int main() {
	fork();
	fork();
	fork();
	printf("hello\n");
	return 0;
}
```

- [ ] A. 3
- [ ] B. 4
- [ ] C. 6
- [x] D. 8

### 2. 有一个程序中有 A,B,C 三个线程同时对一个文件进行读写操作，其中的 A,B 是写线程，只负责往里面写数据，C 是读线程，同时把读取的数据从文件中删除，A 线程单独写满文件需要 10 个小时，B 单独写程序需要 6 小时，C 线程需要 15 小时才能读取完整个文件，不考虑三个线程之间的相互影响的情况下，现在多少小时才能写满文件（）
- [x] A. 5
- [ ] B. 6
- [ ] C. 5.5
- [ ] D. 4.5
- [ ] E. 4.8
- [ ] F. 5.3

### 3. 系统中内存不足程序所需大小，程序就无法执行（）
- [x] A. 错
- [ ] B. 对

### 4. 通常所说的“存储保护”的基本含义是（）
- [ ] A. 防止存储器硬件受损
- [ ] B. 防止程序在内存丢失
- [x] C. 防止程序间相互越界访问
- [ ] D. 防止程序被人偷看

### 5. 下列进程调度算法中，（）可能会出现进程长期得不到调度的情况。
- [ ] A. 非强占式静态优先权法
- [x] B. 强占式静态优先权法
- [ ] C. 时间片轮转调度算法
- [ ] D. 非强占式动态优先权法

### 6. 如果信号量的当前值为－4，则表示系统中在该信号量上有（）个进程等待。
- [x] A. 4
- [ ] B. 3
- [ ] C. 5
- [ ] D. 0

### 7. 设两个进程共用一个临界资源的互斥信号量 mutex=1 ，当 mutex＝-1 时表示（）
- [x] A. 一个进程进入了临界区，另一个进程等待
- [ ] B. 没有一个进程进入临界区
- [ ] C. 两个进程都进入临界区
- [ ] D. 两个进程都在等待

### 8. 若系统中只有用户级线程，则处理机调度单位是（）
- [ ] A. 线程
- [x] B. 进程
- [ ] C. 程序
- [ ] D. 作业

### 9. 一个在线服务器通常需要读取存储着海量数据的数据库。为了提高服务器处理速度，通常需要加cache（缓存），以下场景中不适合使用cache的是（）
- [x] A. 数据库中每条数据被访问的概率近似相等，且独立
- [ ] B. 使用了多线程机制的服务
- [ ] C. 单条线程尺寸太小的数据
- [ ] D. 有着大量访问的服务

### 10. 若某线性表最常用的操作是存取任一指定序号的元素和在最后进行插入和删除运算，则利用（）存储方式最节省时间。
- [x] A. 顺序表
- [ ] B. 双链表
- [ ] C. 带头结点的双循环链表
- [ ] D. 单循环链表