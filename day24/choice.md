### 1. 将 N 条长度均为 M 的有序链表进行合并，合并以后的链表也保持有序，时间复杂度为（）
- [x] A. O(N\*M\*logN)
- [ ] B. O(N\*M)
- [ ] C. O(N)
- [ ] D. O(M)

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 排序步骤如下：<br>
> &#160; &#160; &#160; &#160; （1）取出每一个链表上的第一个元素组建成一个小顶堆，初始化建堆的时间复杂度为 O(N) ；<br>
> &#160; &#160; &#160; &#160; （2）将堆顶最小元素取出，然后把该最小元素所在链表的下一个元素放在堆顶位置（如果该链表为空，那就把堆的最后一个元素放在堆顶位置），接着重建堆，重建堆的时间复杂度为 O(logN) ；<br>
> &#160; &#160; &#160; &#160; （3）重复执行第二步，直到所有链表都为空。<br>
> &#160; &#160; &#160; &#160; 因为初始化建堆只有 `1` 次，而重建堆有 `N*M-N` 次，因此总的时间复杂度为：`O(N)+(N*M-N)*O(logN)`，等价于`O(N*M*logN)`。<br>

### 2. 下设栈 S 的初始状态为空，元素 a,b,c,d,e,f 依次入栈 S ，出栈的序列为 b,d,c,f,e,a ，则栈 S 的容量至少为（）
- [ ] A. 6
- [ ] B. 5
- [ ] C. 4
- [x] D. 3

### 3. 大小为 MAX 的循环队列中，f 为当前队头元素位置，r 为当前队尾元素位置(最后一个元素的位置)，则任意时刻，队列中的元素个数为（）
- [ ] A. r-f
- [x] B. (r-f+MAX+1)%MAX
- [ ] C. r-f+1
- [ ] D. (r-f+MAX)%MAX

### 4. [n!后面有多少个0，6!=1*2*3*4*5*6=720。720后面有1个0，n=10000，求n!（）](https://www.nowcoder.com/questionTerminal/17ec3d482fdb42828f89d73f05d3596e?source=relative)
- [ ] A. 2498
- [x] B. 2499
- [ ] C. 2450
- [ ] D. 2451

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 要计算 n! 后面有多少个0，我们不妨先思考一下这里 0 的具体意义以及它产生的条件？<br>
> &#160; &#160; &#160; &#160; 很明显，0 在这里代表的是一次进位，只有在计算 n! 的过程中有 10 乘入时，才会在 n! 后面出现0，所以本题就可以等价于求出在计算 n! 的过程中能分解出数字 10 的个数。而 10 是一个合数，它可以分解为两个质数之积，即 2\*5 ，所以本题又可等价于求出能分解出 2 的个数和 5 的个数这两个结果之间的较小值。又因为在计算 n! 的过程中，5的倍数的数字个数是小于等于2的倍数的数字个数，所以本题最终就等价于求出从 1 到 n 的所有数字中可以分解出数字5的个数。<br>
> &#160; &#160; &#160; &#160; 当 n=10000 时，有：<br>
> &#160; &#160; &#160; &#160; （1）能分解出1个数字5的个数：10000/5=2000<br>
> &#160; &#160; &#160; &#160; （2）能分解出2个数字5的个数：10000/(5\*5)=400<br>
> &#160; &#160; &#160; &#160; （3）能分解出3个数字5的个数：10000/(5\*5\*5)=80<br>
> &#160; &#160; &#160; &#160; （4）能分解出4个数字5的个数：10000/(5\*5\*5\*5)=16<br>
> &#160; &#160; &#160; &#160; （5）能分解出5个数字5的个数：10000/(5\*5\*5\*5\*5)=3<br>
> &#160; &#160; &#160; &#160; （6）能分解出6个数字5的个数：10000/(5\*5\*5\*5\*5\*5)=0<br>
> &#160; &#160; &#160; &#160; 综上所述，那么从 1 到 10000 的所有数字中一共可以分解出 `2000+400+80+16+3=2499` 个数字5，所以 10000! 后面有 2499 个0。<br>

### 5. 若一棵二叉树具有 12 个度为 2 的结点，6 个度为 1 的结点，则度为 0 的结点个数是（）
- [ ] A. 10
- [ ] B. 11
- [x] C. 13
- [ ] D. 不确定

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 设 n0 为度为0的结点个数，n1 为度为1的结点个数，n2 为度为2的结点个数，那么这棵二叉树的**总结点个数**为 `n0+n1+n2`，**总度数**为 `n0*0+n1*1+n2*2`。此外，对任意一棵二叉树来说，除了根结点以外，每个结点都有一个入度，所以这棵二叉树的**入度之和**为 `总结点个数-1`，而入度之和与总度数相等，所以又有：`n0+n1+n2-1 = n0*0+n1*1+n2*2`，由此可得到：`n0=n2+1`。<br>

### 6. [若将关键字 1,2,3,4,5,6,7 依次插入到初始为空的平衡二叉树 T 中，则 T 中平衡因子为 0 的分支结点的个数是（）](https://www.nowcoder.com/questionTerminal/d18b23d6f00c41eba5aba6587592d531?source=relative)
- [ ] A. 0
- [ ] B. 1
- [ ] C. 2
- [x] D. 3

### 7. 已知小根堆为 8,15,10,21,34,16,12 ，删除关键字 8 之后需重建堆，在此过程中，关键字之间的比较次数是（）
- [ ] A. 1
- [ ] B. 2
- [x] C. 3
- [ ] D. 4

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 删除 8 后，将 12 放到堆顶，第一次是 12 和 15 比较，第二次是 12 和 10 比较并进行交换，第三次是 12 和 16 比较，故一共比较 3 次。<br>

### 8. [已知某个哈希表的 n 个关键字具有相同的哈希值，如果使用二次探测再散列法将这 n 个关键字存入哈希表，至少要进行几次探测（）](https://www.nowcoder.com/questionTerminal/62df46dd871e43a981672ff3f50719cb?orderByHotValue=2&done=0&pos=40&onlyReference=false)
- [ ] A. n-1
- [ ] B. n
- [ ] C. n+1
- [ ] D. n(n+1)
- [x] E. n(n+1)/2
- [ ] F. 1+n(n+1)/2

### 9. 下列选项中，不可能是快速排序第 2 趟排序结果的是（）
- [ ] A. 2,3,5,4,6,7,9
- [ ] B. 2,7,5,6,4,3,9
- [x] C. 3,2,5,4,7,6,9
- [ ] D. 4,2,3,5,7,6,9

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 快排的阶段性排序结果的特点是：第 i 趟排序完成时，至少有 i 个数出现在它们各自最终将要出现的位置上。本题选项中所给的数字排序后为 2,3,4,5,6,7,9 ，通过比对，C 选项中只有数字 9 在最终的位置上，与上述结论不符。<br>

### 10. [设有向图 G=(V,E) ，顶点集 V={V0,V1,V2,V3} ，边集 E={<v0,v1>, <v0,v2>, <v0,v3>, <v1,v3>} 。若从顶点 V0 开始对图进行深度优先遍历，则可能得到的不同遍历序列个数是（）](https://www.nowcoder.com/questionTerminal/b1b530e411e64508b237e19ee8618426?orderByHotValue=1&mutiTagIds=584&page=1&onlyReference=false)
- [ ] A. 2
- [ ] B. 3
- [ ] C. 4
- [x] D. 5
