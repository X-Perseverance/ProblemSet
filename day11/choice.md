### 1. 在32位系统环境，编译选项为4字节对齐，那么 sizeof(A) 和 sizeof(B) 是（）
```c
struct A
{
	int a;
	short b;
	int c;
	char d;
};

struct B
{
	int a;
	short b;
	char c;
	int d;
};
```

- [ ] A. 16,16
- [ ] B. 13,12
- [x] C. 16,12
- [ ] D. 11,16 

### 2. 以下函数中，和其他函数不属于一类的是（）
- [ ] A. fwrite
- [ ] B. putc
- [x] C. pwrite
- [ ] D. putchar
- [ ] E. getline
- [ ] F. scanf

> **【解析】**<br>
> &#160; &#160; &#160; &#160; pwrite是系统调用，其他都属于库函数。<br>

### 3. 当n=5时，下列函数的返回值是（）
```c
int foo(int n) {
	if (n < 2) {
		return n;
	}
	else
		return 2 * foo(n - 1) + foo(n - 2);
}
```

- [ ] A. 5
- [ ] B. 11
- [x] C. 29
- [ ] D. 10 

### 4. 以下程序的输出结果是（）
```c ++
#include <iostream>

void main()
{
	int x = 3, y = 3;
	switch (x % 2) {
	case 1:
		switch (y) {
		case 0:cout << "first";
		case 1:cout << "second"; break;
		default: cout << "hello";
		}
	case 2:cout << "third";
	}
}
```

- [ ] A. second third
- [ ] B. hello
- [ ] C. first second
- [x] D. hellothird

### 5. 下列代码试图打印数字1-9的全排列组合，其中run函数中缺失的部分应该依次为（）
```c
#include <stdio.h>

#define N 9

int x[N];
int count = 0;

void dump() {
	int i = 0;
	for (i = 0; i < N; i++) {
		printf("%d", x[i]);
	}
	printf("\n");
}

void swap(int a, int b) {
	int t = x[a];
	x[a] = x[b];
	x[b] = t;
}

void run(int n) {
	int i;
	if (N - 1 == n) {
		dump();
		count++;
		return;
	}
	for (i = ___; i < N; i++) {
		swap(___, i);
		run(n + 1);
		swap(___, i);
	}
}

int main()
{
	int i;
	for (i = 0; i < N; i++) {
		x[i] = i + 1;
	}
	run(0);
	printf("* Total: %d\n", count);
}
```

- [ ] A. n+1, n, n+1
- [ ] B. n+1, n, n
- [x] C. n, n, n
- [ ] D. n, n+1, n+1
- [ ] E. n+1, n+1, n+1
- [ ] F. n, n, n+1

### 6. 下列哪个用法哪个是错误的（）
- [ ] A. int *a;
- [ ] B. extern const int array[256];
- [x] C. const int &ra;
- [ ] D. typedef void (*FUN)();

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 被const修饰的变量和引用在定义时都必须进行初始化。<br>

### 7. 在重载一个运算符为成员函数时，其参数表中没有任何参数，这说明该运算符是（）
- [ ] A. 无操作数的运算符
- [ ] B. 二元运算符
- [x] C. 前缀一元运算符
- [ ] D. 后缀一元运算符

### 8. 若PAT是一个类，则程序运行时，语句`PAT (*ad)[3];`调用PAT的构造函数的次数是（）
- [ ] A. 2
- [ ] B. 3
- [x] C. 0
- [ ] D. 1

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 在本题中，ad是一个指向有着三个PAT元素的数组的指针，这里只是声明了指针，虽然指针指向的数组有三个PAT对象，但是并没有实例化其中的对象，所以并没有调用构造函数。<br>

### 9. [以下程序输出结果是（）](https://www.nowcoder.com/questionTerminal/e4d5fe27a85d43548171f32b3bc8501a)
```c ++
class A
{
public:
	virtual void func(int val = 1)
	{
		std::cout << "A->" << val << std::endl;
	}
	virtual void test()
	{
		func();
	}
};

class B : public A
{
public:
	void func(int val = 0)
	{
		std::cout << "B->" << val << std::endl;
	}
};

int main(int argc, char* argv[])
{
	B*p = new B;
	p->test();

	return 0;
}
```

- [ ] A. A->0
- [x] B. B->1
- [ ] C. A->1
- [ ] D. B->0
- [ ] E. 编译出错
- [ ] F. 以上都不对

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 虚函数是动态绑定，而缺省参数值却是静态绑定。 当调用一个定义于派生类内的虚函数时，使用基类为它所指定的缺省参数值。<br>

### 10. 下面程序的输出是（）
```c ++
class A
{
public:
	void foo()
	{
		printf("1");
	}
	virtual void fun()
	{
		printf("2");
	}
};

class B : public A
{
public:
	void foo()
	{
		printf("3");
	}
	void fun()
	{
		printf("4");
	}
};

int main()
{
	A a;
	B b;
	A *p = &a;
	p->foo();
	p->fun();
	p = &b;
	p->foo();
	p->fun();
	A *ptr = (A *)&b;
	ptr->foo();
	ptr->fun();

	return 0;
}
```

- [ ] A. 121434
- [x] B. 121414
- [ ] C. 121232
- [ ] D. 123434
