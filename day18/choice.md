### 1. 使用 printf 函数打印一个 double 类型的数据，要求：输出为10进制，输出左对齐30个字符，4位精度。以下哪个选项是正确的（）
- [ ] A. %-30.4e
- [ ] B. %4.30e
- [x] C. %-30.4f
- [ ] D. %-4.30f

### 2. malloc 函数进行内存分配是在什么阶段（）
- [ ] A. 编译阶段
- [ ] B. 链接阶段
- [ ] C. 装载阶段
- [x] D. 执行阶段

### 3. 函数作用：将整型数组p中n个数据增大。以下代码的实现有错误，下面哪句话的表述是正确的（）
```c
void increment_ints(int p[], int n)
{
	assert(p != NULL); /* 确保p不为空指针 */
	assert(n >= 0); /* 确保n不为负数 */
	while (n) /* 循环n次. */
	{
		*p++; /* 增大p*/
		p++, n--; /* p指向下一位，n减1 */
	}
}
```

- [x] A. *p++ 使得 p 在解引用之前增大，应该改为 (*p)++
- [ ] B. 数组的值是一个不能改变的值，所以 p 不能直接被修改，应该使用一个和 p 相关联的指针来完成这个操作
- [ ] C. while 循环的条件必须是一个布尔类型的表达式，表达式应该为 n!=0
- [ ] D. p 不应该定义为变长的数组，参数中不应该包含参数 n

### 4. 如下函数的 f(1) 的值为（）
```c
int f(int n) {
	static int i = 1;
	if (n >= 5)
		return n;
	n = n + i;
	i++;
	return f(n);
}
```

- [ ] A. 5
- [ ] B. 6
- [x] C. 7
- [ ] D. 8

### 5.下列给定程序中，函数 fun 的功能是：把形参 a 所指数组中的最小值放在元素 a[0] 中，接着把 a 所指数组中的最大值放在 a[1] 元素中；再把a所指数组元素中的次小值放在 a[2] 中，把a索取数组元素中的次大值放在 a[3]，以此类推。例如：若a所指数组中的数据最初排列为：9,1,4,2,3,6,5,8,7；按规则移动后，数据排列为：1,9,2,8,3,7,4,6,5。形参 n 中存放 a 所指数组中数据的个数。规定 fun 函数中的 max 存放的当前所找的最大值，px 存放当前所找最大值得下标。请在程序的下画线处填入正确的内容并将下画线删除，使程序得出正确的结果。（）
```c
#include <stdio.h>

#define N 9

void fun(int a[], int n)
{
	int i, j, max, min, px, pn, t;
	for (i = 0; i < n - 1; i += 2) {
		max = min = _____;
		px = pn = i;
		for (j = i + 1; j < n; j++) {
			if (max < _____) {
				max = a[j];
				px = j;
			}
			if (min > _____) {
				min = a[j];
				pn = j;
			}
		}
		if (pn != i) {
			t = a[i];
			a[i] = min;
			a[pn] = t;
			if (px == i)
				px = pn;
		}
		if (px != i + 1) {
			t = a[i + 1];
			a[i + 1] = max;
			a[px] = t;
		}
	}
}

int main()
{
	int b[N] = { 9, 1, 4, 2, 3, 6, 5, 8, 7 };

	printf("\nThe original data:\n");
	for (int i = 0; i < N; i++)
		printf("%4d", b[i]);
	printf("\n");

	fun(b, N);

	printf("\nThe data after mocinng \n");
	for (int i = 0; i < N; i++)
		printf("%4d", b[i]);
	printf("\n");
}
```

- [ ] A. 0 a[i] a[i]
- [x] B. a[i] a[j] a[j]
- [ ] C. 0 a[j] a[j]
- [ ] D. a[i] a[i] a[i]

### 6. 下面说法正确的是（）
- [ ] A. C++ 已有的任何运算符都可以重载
- [x] B. const 对象只能调用 const 类型成员函数
- [ ] C. 构造函数和析构函数都可以是虚函数
- [ ] D. 函数重载返回值类型必须相同

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 选项A，5个不可重载的运算符：`.`，`.*`，`::`，`?:`，`sizeof`<br>
> &#160; &#160; &#160; &#160; 选项C，构造函数不能为虚函数<br>
> &#160; &#160; &#160; &#160; 选项D，函数重载返回值类型不必相同<br>

### 7. 下面关于迭代器失效的描述哪个是错误的（）
- [x] A. vector的插入操作不会导致迭代器失效
- [ ] B. map的插入操作不会导致迭代器失效
- [ ] C. vector的删除操作只会导致指向被删除元素及后面的迭代器失效
- [ ] D. map的删除操作只会导致指向被删除元素的迭代器失效

### 8. 下面哪一个是 sort 的 template 的正确写法（）
- [ ] A. void sort(class A first，class A last，class B pred)
- [ ] B. void template(class A，class B)sort(A first，A last，B pred)
- [ ] C. template<class A><class B> void sort(A first，A last，B pred)
- [x] D. template<class A，class B> void sort(A first，A last，B pred)

### 9. 以下程序的运行结果是（）
```c
void main()
{
	char a[] = "programming", b[] = "language";
	char *p1, *p2;
	int i;
	p1 = a, p2 = b;
	for (i = 0; i < 7; i++) {
		if (*(p1 + i) == *(p2 + i))
			printf("%c", *(p1 + i));
	}
}
```

- [ ] A. gm
- [ ] B. rg
- [ ] C. or
- [x] D. ga

### 10. 下列程序的输出结果（）
```c ++
#include <iostream>

using namespace std;

class A {
public:
	void print() {
		cout << "A:print()";
	}
};

class B : private A {
public:
	void print() {
		cout << "B:print()";
	}
};

class C : public B {
public:
	void print() {
		A::print();
	}
};

int main()
{
	C b;
	b.print();
	return 0;
}
```

- [ ] A. A:print()
- [ ] B. B:print()
- [x] C. 编译出错
