### 1. 以下说法正确的是（）
```c
void swap_int(int *a, int *b) {
	*a = *a + *b;
	*b = *a - *b;
	*a = *a - *b;
}
```

- [ ] A. 结果不正确，因为会溢出，用位与的方式就没问题
- [x] B. 结果正确，即使会溢出
- [ ] C. 结果正确，不会溢出
- [ ] D. 其他选项都不对

### 2. 若有定义 `int (*pt)[3];` 则下列说法正确的是（）
- [ ] A. 定义了基类型为 int 的三个指针变量
- [ ] B. 定义了基类型为 int 的具有三个元素的指针数组pt
- [ ] C. 定义了一个名为 *pt 具有三个元素的整型数组
- [x] D. 定义了一个名为 pt 的指针变量，它可以指向每行有三个整数元素的二维数组 

### 3. [对于下面的说法，正确的是（）](https://www.nowcoder.com/questionTerminal/1277288d00a64c1ca58736345fecbdab?from=relative)
- [ ] A. 对于 struct X { short s; int i; char c; }，sizeof(X) 的值等于 sizeof(s) + sizeof(i) + sizeof(c)
- [ ] B. 对于某个double变量 a，可以使用 a == 0.0 来判断其是否为零
- [ ] C. 初始化方式 char a[14] = "Hello, world!"; 和初始化方式 char a[14]; a = "Hello, world!"; 的效果相同
- [ ] D. 在gcc编译器下，对于 int i = 3; printf("%d %d", ++i, ++i)，运行输出为：4 5
- [ ] E. 选项A、B、C、D中至少有两个是正确的
- [x] F. 以上选项均不正确

### 4. 下列代码的输出是（）（注：print 已经声明过）
```c
main() {
	char str[] = "Geneius";
	print(str);
}

print(char *s) {
	if (*s) {
		print(++s);
		printf("%c", *s);
	}
}
```

- [x] A. suiene
- [ ] B. neius
- [ ] C. run-time error
- [ ] D. suieneG

> **【解析】**：<br>
> &#160; &#160; &#160; &#160; （1）*s为G，++s 后执行print(e)，printf(`e`)入栈；<br>
> &#160; &#160; &#160; &#160; （2）*s为e，++s 后执行print(n)，printf(`n`)入栈；<br>
> &#160; &#160; &#160; &#160; （3）*s为n，++s 后执行print(e)，printf(`e`)入栈；<br>
> &#160; &#160; &#160; &#160; （4）*s为e，++s 后执行print(i)，printf(`i`)入栈；<br>
> &#160; &#160; &#160; &#160; （5）*s为i，++s 后执行print(u)，printf(`u`)入栈；<br>
> &#160; &#160; &#160; &#160; （6）*s为u，++s 后执行print(s)，printf(`s`)入栈；<br>
> &#160; &#160; &#160; &#160; （7）*s为s，++s 后执行print('\0)，printf(`'\0'`)入栈；<br>
> &#160; &#160; &#160; &#160; （8）*s为 '\0'，递归结束，从栈顶向下依次执行 printf(*s)，那么最后的结果为：`'\0'suiene`。<br>

### 5. 写出下面程序的输出结果（）
```c ++
#include <iostream>

using namespace std;

class A
{
public:
	void FuncA()
	{
		printf("FuncA called\n");
	}
	virtual void FuncB()
	{
		printf("FuncB called\n");
	}
};

class B : public A
{
public:
	void FuncA()
	{
		A::FuncA();
		printf("FuncAB called\n");
	}
	virtual void FuncB()
	{
		printf("FuncBB called\n");
	}
};

int main()
{
	B b;
	A *pa;
	pa = &b;
	A *pa2 = new A;

	pa->FuncA();
	pa->FuncB();
	pa2->FuncA();
	pa2->FuncB();

	delete pa2;

	return 0;
}
```

- [ ] A. FuncA called FuncB called FuncA called FuncB called
- [x] B. FuncA called FuncBB called FuncA called FuncB called
- [ ] C. FuncA called FuncBB called FuncAB called FuncBB called
- [ ] D. FuncAB called FuncBB called FuncA called FuncB called

### 6. 以下程序输出是（）
```c ++
#include <iostream>

using namespace std;

int main(void)
{
	const int a = 10;
	int * p = (int *)(&a);
	*p = 20;
	cout << "a = " << a << ", *p = " << *p << endl;

	return 0;
}
```

- [ ] A. 编译阶段报错运行阶段报错
- [ ] B. a = 10, *p = 10
- [ ] C. a = 20, *p = 20
- [x] D. a = 10, *p = 20
- [ ] E. a = 20, *p = 10

> **【解析】**：<br>
> &#160; &#160; &#160; &#160; 上述代码在执行时会由于编译器优化而导致出现 **常量折叠** 现象，所谓的常量折叠意思就是在编译器进行语法分析的时候，将常量表达式计算求值，并用求得的值来替换表达式，放入常量表。<br>
> &#160; &#160; &#160; &#160; 对上述代码来说，在预处理阶段，编译器会把用 const 修饰的变量 a 以具体值 10 替换掉（和宏定义有些类似），以优化代码。但在运行阶段，该变量内存空间里的内容确实改变了。<br>

### 7. [以下关于 STL 的描述中，（）是错的。](https://www.nowcoder.com/questionTerminal/e38151104a6447ef83649faa4abe4f68?from=relative)
- [ ] A. STL 容器是线程不安全的
- [ ] B. 当容量不够时，vector 内部内存扩展方式是翻倍
- [x] C. std::sort 是稳定排序
- [ ] D. std::bitset 不是一个 STL 容器
- [ ] E. std::stack 默认是用 deque 实现的
- [ ] F. std::string 中可以存储多个 '\0' 字符

### 8. 以下代码共调用多少次拷贝构造函数（）
```c ++
Widget f(Widget u)
{
	Widget v(u);
	Widget w = v;
	return w;
}

main() {
	Widget x;
	Widget y = f(f(x));
}
```

- [ ] A. 1
- [ ] B. 3
- [ ] C. 5
- [x] D. 7

### 9. 以下代码有什么问题（）
```c ++
struct Test
{
	Test(int) {}
	Test() {}
	void fun() {}
};

void main(void)
{
	Test a(1);
	a.fun();
	Test b();
	b.fun();
}
```

- [x] A. b.fun() 会出错
- [ ] B. Test 结构的定义中应该加上 public 修饰符，这样 main 函数中才能调用改类的方法
- [ ] C. Test(int) {} 应该改成 Test(int a) {}
- [ ] D. 以上说法都不正确

> **【解析】**：<br>
> &#160; &#160; &#160; &#160; 程序中 `Test b();` 只是声明了一个函数 b，其返回值类型为 Test，而不是创建了一个Test类对象 b，所以当用 b 去调用 fun() 会出错。<br>

### 10. 在32位环境下，以下程序的输出结果是（）
```c ++
#include<iostream>

using namespace std;

class Base {
public:
	virtual int foo(int x) {
		return x * 10;
	}
	int foo(char x[14]) {
		return sizeof(x) + 10;
	}
};

class Derived : public Base {
	int foo(int x) {
		return x * 20;
	}
	virtual int foo(char x[10]) {
		return sizeof(x) + 20;
	}
};

int main()
{
	Derived stDerived;
	Base *pstBase = &stDerived;
	char x[10];
	printf("%d\n", pstBase->foo(100) + pstBase->foo(x));

	return 0;
}
```

- [ ] A. 2000
- [ ] B. 2004
- [x] C. 2014
- [ ] D. 2024
