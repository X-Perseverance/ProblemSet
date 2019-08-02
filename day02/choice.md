### 1. 有以下定义：`int a[10]; char b[80];` 函数声明为：`void sss(char[], int[]);` 则正确的函数调用形式是（）

- [ ] A. sss(a,b);
- [ ] B. sss(char b[],int a[]);
- [ ] C. sss(b[],a[]);
- [x] D. sss(b,a);

### 2. 数组 a 的定义语句为 `float a[3][4];` 下列（）是对数组元素不正确的引用方法
- [ ] A. `a[i][j]`
- [ ] B. `*(a[i]+j)`
- [ ] C. `*(*(a+i)+j)`
- [x] D. `*(a+i*4+j)`

### 3. 下面叙述错误的是（）
```c
char acX[]=”abc”;
char acY[]={‘a’,’b’,’c’};
char *szX=”abc”;
char *szY=”abc”;
```
- [ ] A. acX与acY的内容可以修改
- [ ] B. szX与szY指向同一个地址
- [ ] C. acX占用的内存空间比acY占用的大
- [x] D. szX的内容修改后，szY的内容也会被更改

### 4. 下列代码的运行结果是（）
```c
int a[]={1,2,3,4};
int *b=a;
*b+=2;
*(b+2)=2;
b++;
printf(“%d,%d\n”,*b,*(b+2));
```

- [ ] A. 1,3
- [ ] B. 1,2
- [x] C. 2,4
- [ ] D. 3,2

### 5. 在32位CPU上选择缺省对齐的情况下，有如下结构体定义，则 `sizeof(struct A)` 的值为（）
```c
struct A{
	unsigned a : 19;
	unsigned b : 11;
	unsigned c : 4;
	unsigned d : 29;
	char index;
};
```

- [ ] A. 9
- [ ] B. 12
- [x] C. 16
- [ ] D. 20

> **【分析】**<br>
> &#160; &#160; &#160; &#160; 通过题目可知，该结构体中含有位段，而位段的空间是按照需要以4个字节或1个字节的方式来开辟的。对该题来说，由于变量 a，b，c，d 的类型都为 unsigned，所以位段的空间以每次4个字节的方式开辟，具体空间分布如下图所示：<br>

![ ]()

### 6.

