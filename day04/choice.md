### 1. 用变量a给出下面的定义：一个有10个指针的数组，该指针指向一个函数，该函数有一个整形参数并返回一个整型数（）
- [ ] A. int *a[10];
- [ ] B. int (*a)[10];
- [ ] C. int (*a)(int);
- [x] D. int (*a[10])(int);

### 2. 对于`int* pa[5];`的描述，以下哪个选项是正确的（）
- [x] A. pa是一个具有5个元素的指针数组，每个元素是一个int类型的指针
- [ ] B. pa是一个指向数组的指针，所指向的数组是5个int类型的元素
- [ ] C. pa[5]表示某个数的第5个元素的值
- [ ] D. pa是一个指向某个数组中第5个元素的指针，该元素是int类型的变量

### 3. 下列程序执行后，输出的结果为()
```c
#include<stdio.h>

int cnt=0;
int fib(int n)
{
	cnt++;
	if(n == 0)
		return 1;
	else if(n == 1)
		return 2;
	else
		return fib(n-1)+fib(n-2);
}

void main()
{
	fib(8);
	printf("%d", cnt);
}
```

- [ ] A. 41
- [x] B. 67
- [ ] C. 109
- [ ] D. 177

> **【技巧】**<br>
> &#160; &#160; &#160; &#160; 一般而言，对于这种嵌套递归的计算题来说，若是采取常规的自上而下的思想去解题，那么计算量只会越来越多，并且很多都是重复计算，就拿这道题来说，要计算f(8)就要先计算出f(7)和f(6)，而要计算f(7)就要先计算出f(6)和f(5)，此时我们会发现f(6)要计算两次，若继续下去，我们可能会深陷于此。所以我们要反其道而行，应采取**自下而上**的思想，具体推演如下表所示：<br>

| n | f(n) | 计算次数 |
| :--: | :--: | :--: |
| 0 | f(0) | 1 |
| 1 | f(1) | 1 |
| 2 | 1+f(1)+f(0) | 3 |
| 3 | 1+f(2)+f(1) | 5 |
| 4 | 1+f(3)+f(2) | 9 |
| 5 | 1+f(4)+f(3) | 15 |
| 6 | 1+f(5)+f(4) | 25 |
| 7 | 1+f(6)+f(5) | 41 |
| 8 | 1+f(7)+f(6) | 67 |

> &#160; &#160; &#160; &#160; 通过观察上述图表，我们发现：<br>
> &#160; &#160; &#160; （1）采用自下而上的思想去解题，计算量少，并且并不会有重复计算；<br>
> &#160; &#160; &#160; （2）分析第二列的计算式，不难看出这道题是一个**菲波那切数列**的变形。从计算f(2)开始，每次的计算式都是前两次计算值之和再加一，而加一正是因为每次计算时的 `cnt++;` ，通过这个规律，后面的计算就容易多了。<br>

### 4. 以下C语言指令运行结果是什么（）
```c
int a[5] = {1, 3, 5, 7, 9};
int *p = (int*)(&a+1);
printf("%d,%d", *(a+1), *(p-1));
```

- [ ] A. 2,1
- [ ] B. 3,1
- [x] C. 3,9
- [ ] D. 运行时崩溃

### 5. 以下哪个选项一定可以将flag的第二个bit置0（）
- [x] A. flag &= ~2
- [ ] B. flag |= 2
- [ ] C. flag ^= 2
- [ ] D. flag >>= 2

### 6. print()函数是一个类的常成员函数，它无返回值，下列表示中正确的是()
- [ ] A. const void print();
- [ ] B. void const print();
- [x] C. void print() const;
- [ ] D. void print(const);

### 7. 以下关于纯虚函数的说法，正确的是()
- [x] A. 声明纯虚函数的类不能实例化
- [ ] B. 声明纯虚函数的类成虚基类
- [ ] C. 子类必须实现基类的
- [ ] D. 纯虚函数必须是空函数

### 8. 下列有关this指针使用方法的叙述正确的是（）
- [ ] A. 保证基类保护成员在子类中可以被访问
- [ ] B. 保证基类私有成员在子类中可以被访问
- [ ] C. 保证基类共有成员在子类中可以被访问
- [x] D. 保证每个对象拥有自己的数据成员，但共享处理这些数据的代码

### 9. 下列情况中，不会调用拷贝构造函数的是（）
- [ ] A. 用一个对象去初始化同一个类的另一个新对象时
- [x] B. 将类的一个对象赋值给该类的另一个对象时
- [ ] C. 函数的形参对象，调用函数进行形参和实参结合时
- [ ] D. 函数的返回值是类的对象，函数执行返回调用时

### 10. 下面程序输出结果是什么（）
```c++
#include <iostream>

using namespace std;

class A {
public:
	A(char *s) {
		cout << s << endl;
	}
	~A() {}
};

class B :virtual public A {
public:
	B(char *s1, char*s2) :A(s1) {
		cout << s2 << endl;
	}
};

class C :virtual public A {
public:
	C(char *s1, char*s2) :A(s1) {
		cout << s2 << endl;
	}
};

class D :public B, public C {
public:
	D(char *s1, char *s2, char *s3, char *s4) :B(s1, s2), C(s1, s3), A(s1) {
		cout << s4 << endl;
	}
};

int main() {
	D *p=new D("class A","class B","class C","class D");
	delete p;
	return 0;
}
```

- [x] A. class A class B class C class D
- [ ] B. class D class B class C class A
- [ ] C. class D class C class B class A
- [ ] D. class A class C class B class D
