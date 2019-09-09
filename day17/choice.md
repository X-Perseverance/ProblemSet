### 1. 以下代码执行之后 ptr 指向的内容是（）
```c
char *ptr;
char myString[] = "abcdefg";
ptr = myString;
ptr += 5;
```

- [ ] A. Compiler error
- [x] B. f
- [ ] C. efg
- [ ] D. defg

### 2. 已知 `int a[]={1,2,3,4,5}; int*p[]={a,a+1,a+2,a+3}; int **q=p;` 那么表达式 `*(p[0]+1)+**(q+2)` 的值是（）
- [x] A. 5
- [ ] B. 6
- [ ] C. 7
- [ ] D. 8
- [ ] E. 4
- [ ] F. 9

### 3. 以下代码的输出结果是（）
```c
char *p = "abc";
char *q = "abc123";
while (*p = *q)
	print("%c %c", *p, *q);
```

- [ ] A. aabbcc
- [ ] B. aabbcc123
- [ ] C. abcabc123
- [ ] D. 代码段错误

> **【解析】**<br>
> &#160; &#160; &#160; &#160; `*p = *q` 这句代码错误，因为字符串常量不能被重新赋值。<br>

### 4. 假设在一个 32 位 little endian 的机器上运行下面的程序，结果是（）
```c
#include <stdio.h>

int main() {
	long long a = 1, b = 2, c = 3;
	printf("%d,%d,%d\n", a, b, c);

	return 0;
}
```
- [ ] A. 1,2,3
- [x] B. 1,0,2
- [ ] C. 1,3,2
- [ ] D. 3,2,1

### 5. 下列给定程序中，函数 fun 的功能是：求 ss 所指字符串数组中长度**最短**的字符串所在的行下标，作为函数值返回，并把其串长放在形参n所指的变量中。ss 所指字符串数组中共有 M 个字符串，且串长小于 N。请在程序的下画线处填入正确的内容并将下画线删除，使程序得出正确的结果。（）
```c
#define M 5
#define N 20

int fun(char(*ss)[N], int *n)
{
	int i, k = 0, len = N;
	for (i = 0; i < _____; i++)
	{
		len = strlen(ss[i]);
		if (i == 0)
			*n = len;
		if (len _____ * n)
		{
			*n = len;
			k = i;
		}
	}
	return (_____);
}

void main()
{
	char ss[M][N] = { "shanghai", "guangzhou", "beijing", "tianjing", "chongqing" };
	int n, k, i;
	printf("\nThe originalb stringsare:\n");
	for (i = 0; i < M; i++)
		puts(ss[i]);

	k = fun(ss, &n);
	printf("\nThe length of shortest string is: % d\n", n);
	printf("\nThe shortest string is: % s\n", ss[k]);
}
```

- [ ] A. N, <, k
- [ ] B. N, >, k
- [x] C. M, <, k
- [ ] D. M, >, k

### 6. 调用一成员函数时, 使用动态联编的情况是（）
- [ ] A. 通过对象调用一虚函数
- [x] B. 通过指针或引用调用一虚函数
- [ ] C. 通过对象调用静态函数
- [ ] D. 通过指针或引用调用一静态函数

### 7. 如何捕获异常可以使得代码通过编译（）
```c ++
class A {
public:
	A() {}
};

void foo() {
	throw new A;
}
```

- [ ] A. catch (A&& x)
- [x] B. catch (A* x)
- [ ] C. catch (A& x)
- [ ] D. 以上都是

### 8. 下列代码可以通过编译吗？如何修改使其通过编译？（）
```c ++
template <class T>
struct sum {
	static void foo(T op1, T op2) {
		cout << op1 << op2;
	}
};

sum::foo(1, 3);
```

- [ ] A. 编译通过
- [ ] B. 应该去掉 static 关键字
- [x] C. 调用应该如下：`sum<int>::foo(1, 3)`
- [ ] D. 调用应该如下：`sum::<int>foo(1, 3)`

### 9. 下面这段程序的输出是什么（）
```c ++
class A {
public:
	A() { p(); }
	virtual void p() { print("A") }
	virtual ~A() { p(); }
};

class B :public A {
public:
	B() { p(); }
	void p() { print("B") }
	~B() { p(); }
};

int main(int, char**) {
	A* a = new B();
	delete a;
}
```

- [ ] A. AABB
- [ ] B. BBAA
- [ ] C. ABAB
- [x] D. ABBA

### 10. 下面程序的输出结果是（）
```c ++
#include <iostream>

using namespace std;

class A {
public:
	~A() {
		cout << "~A()";
	}
};

class B {
public:
	virtual ~B() {
		cout << "~B()";
	}
};

class C : public A, public B {
public:
	~C() {
		cout << "~C()";
	}
};

int main() {
	C * c = new C;
	B * b1 = dynamic_cast<B *>(c);
	A * a2 = dynamic_cast<A *>(b1);
	delete a2;

	return 0;
}
```

- [ ] A. ~C()~B()~A()
- [ ] B. ~C()~A()~B()
- [ ] C. A B 都有可能
- [x] D. 以上都不对

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 在 main 函数中，先通过 new 调用构造函数创建了类 C 的对象，接着定义了两个不同对象的指针变量，最后通过 delete 调用析构函数释放了 a2，由于基类 A 的析构函数不是虚函数，那么只会调用 A 的析构函数，输出 `~A()`，但此时并没有调用 C 的析构函数，而之前又创建了一个类 C 的对象，所以会产生内存泄露问题。倘若给 A 的析构函数加上 virtual，那么就会先调用派生类的析构函数，再调用基类的析构函数，输出 `~C()~B()~A()`，从而防止了内存泄露。<br>
