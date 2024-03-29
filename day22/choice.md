### 1. 若某线性表最常用的操作是存取任一指定序号的元素和在最后进行插入和删除运算，则利用（）存储方式最节省时间
- [x] A. 顺序表
- [ ] B. 双链表
- [ ] C. 带头结点的双循环链表
- [ ] D. 单循环链表

### 2. 下列数据结构具有记忆功能的是（）
- [ ] A. 队列
- [ ] B. 循环队列
- [x] C. 栈
- [ ] D. 顺序表

### 3. 循环两列放在一维数组 A[0…M-1] 中， end1 指向队头元素， end2 指向队尾元素的后一个位置。假设队列两端均可进行入队和出队操作，队列中最多能容纳 M-1 个元素。初始时为空，下列判断队空和队满的条件中，正确的是（）
- [x] A. 队空：end1==end2；队满：end1==(end2+1)modM
- [ ] B. 队空：end1==end2；队满：end2==(end1+1)mod(M-1)
- [ ] C. 队空：end2==(end1+1)modM；队满：end1==（end2+1）modM
- [ ] D. 队空：end1==（end2+1）modM；队满：end2==(end1+1)mod(M-1)

### 4. [对递归程序的优化的一般的手段为（）](https://www.nowcoder.com/questionTerminal/c7c14a2d52ea458c95fed1e6198ca4e8?orderByHotValue=2&page=1&onlyReference=false)
- [x] A. 尾递归优化
- [ ] B. 循环优化
- [ ] C. 堆栈优化
- [ ] D. 停止值优化

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 尾递归是指在函数返回的时候调用函数自身，并且 return 语句不能包含任何表达式。这样编译器或者解释器就可以对尾递归做优化，使递归无论调用多少次，都只占用一个栈帧，不会出现栈溢出的情况。但遗憾的是，大多数的编程语言都没有针对尾递归做优化。<br>

### 5. 将一颗有 100 个结点的完全二叉树从根这一层开始，每一层从左到右依次对结点进行编号，根节点编号为 1 ，则编号为 98 的节点的父节点编号为（）
- [ ] A. 47
- [ ] B. 48
- [x] C. 49
- [ ] D. 50

### 6. 将一棵二叉树的根结点放入队列，然后递归的执行如下操作，将出队结点所有子结点加入队。以上操作可以实现哪种遍历（）
- [ ] A. 前序遍历
- [ ] B. 中序遍历
- [ ] C. 后序遍历
- [x] D. 层序遍历

### 7. 有 1000 个无序的整数，希望使用最快的方式找出前 50 个最大的，最佳的选择是（）
- [ ] A. 冒泡排序
- [ ] B. 基数排序
- [x] C. 堆排序
- [ ] D. 快速排序

### 8. 以下数据结构说法，错误的是（）
- [ ] A. 红黑树插入操作的平均时间复杂度为O(logn)，最坏时间复杂度为O(logn)
- [ ] B. B+树插入操作的平均时间复杂度为O(logn)，最坏时间复杂度为O(logn)
- [x] C. Hash表插入操作的平均时间复杂度为O(logn)，最坏时间复杂度为O(n)
- [ ] D. 排序链表插入操作的平均时间复杂度为O(n)，最坏时间复杂度为O(n)

> **【解析】**<br>
> &#160; &#160; &#160; &#160; Hash表插入操作的平均时间复杂度为O(1)，最坏时间复杂度为O(n)。<br>

### 9. 将两个各有n个元素的有序表归并成一个有序表，最少的比较次数是（）
- [ ] A. 2n
- [ ] B. 2n-1
- [ ] C. n-1
- [x] D. n

### 10. [设图 G 的相邻矩阵如下，则 G 的顶点数和边数分别为（）](https://www.nowcoder.com/questionTerminal/bf9388cb9d5d4057a80f14258282cdd6?source=relative)
&#160; &#160; &#160; &#160; 0 1 1 1 1<br>
&#160; &#160; &#160; &#160; 1 0 1 0 0<br>
&#160; &#160; &#160; &#160; 1 1 0 1 1<br>
&#160; &#160; &#160; &#160; 1 0 1 0 1<br>
&#160; &#160; &#160; &#160; 1 0 1 1 0<br>

- [x] A. 5,8
- [ ] B. 4,10
- [ ] C. 5,6
- [ ] D. 4,5

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 待解决......<br>
