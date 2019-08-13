### 1. 下面关于“指针”的描述不正确的是（）
- [x] A. 当使用free释放掉一个指针内容后，指针变量的值被置为NULL
- [ ] B. 32位系统下任何类型指针的长度都是4个字节
- [ ] C. 指针的数据类型声明的是指针实际指向内容的数据类型
- [ ] D. 野指针是指向未分配或者已经释放的内存地址

> **【分析】**<br>
> &#160; &#160; &#160; &#160; 对于选项A，free之后的指针仍然指向原来的地址，并不是NULL，但是此时该指针已经成为了一个野指针，因为该地址处的内容是一个随机值，是不确定的，为了防止使用该指针所造成的危险，一般建议释放后再手动置NULL。

### 2. 以下程序统计给定输入中每个大写字母的出现次数(不需要检查输入合法性)。以下能补全程序，正确功能的选项是（）
```c
void AlphabetCounting(char a[], int n) {
	int count[26] = {}, i, kind = 0;
	for (i = 0; i < n; ++i) (__1__);
	for (i = 0; i < 26; ++i) {
		if (++kind > 1) putchar(';');
		printf("%c=%d", (__2__));
	}
}
```

- [ ] A. ++count[a[i]-'Z'];&#160; &#160; 'Z'-i,count['Z'-i]
- [ ] B. ++count['A'-a[i]];&#160; &#160; 'A'+i,count[i]
- [ ] C. ++count[i];&#160; &#160; i,count[i]
- [x] D. ++count['Z'-a[i]];&#160; &#160; 'Z'-i,count[i]
- [ ] E. ++count[a[i]];&#160; &#160; 'A'+i,count[a[i]]

### 3. 下列关于C/C++的宏定义，不正确的是（）
- [ ] A. 宏定义不检查参数正确性，会有安全隐患
- [x] B. 宏定义的常量更容易理解，如果可以使用宏定义常量的话，要避免使用const常量
- [ ] C. 宏的嵌套定义过多会影响程序的可读性，而且很容易出错
- [ ] D. 相对于函数调用，宏定义可以提高程序的运行效率

### 4. 下面代码会输出（）
```c
int main() {
	int a[4] = {1, 2, 3, 4};
	int *ptr = (int*)(&a + 1);
	printf("%d", *(ptr - 1));
}
```

- [x] A. 4
- [ ] B. 1
- [ ] C. 2
- [ ] D. 3

### 5. 请找出下面程序中有哪些错误（）
```c
int main()
{
	int i = 10;
	int j = 1;
	const int *p1; //(1)
	int const *p2 = &i; //(2)
	p2 = &j; //(3)
	int *const p3 = &i; //(4)
	*p3 = 20; //(5)
	*p2 = 30; //(6)
	p3 = &j; //(7)
	return 0;
}
```

- [ ] A. 1,2,3,4,5,6,7
- [ ] B. 1,3,5,6
- [x] C. 6,7
- [ ] D. 3,5

### 6. 在公有派生的情况下，派生类中定义的成员函数只能访问原基类的（）
- [ ] A. 公有成员和私有成员
- [ ] B. 私有成员和保护成员
- [x] C. 公有成员和保护成员
- [ ] D. 私有成员，保护成员和公有成员

### 7. 假定有类AB，有相应的构造函数定义，能正确执行 `AB a(4), b(5), c[3], *p[2]={&a,&b};` 语句，请问执行完此语句后共调用该类的构造函数次数为（）
- [x] A. 5
- [ ] B. 4
- [ ] C. 3
- [ ] D. 9

### 8. 关于函数的描述正确的是（）
- [ ] A. 虚函数是一个static型的函数
- [ ] B. 派生类的虚函数与基类的虚函数具有不同的参数个数和类型
- [ ] C. 虚函数是一个非成员函数
- [x] D. 基类中说明了虚函数后，派生类中起对应的函数可以不必说明为虚函数

### 9. 有如下程序，执行后输出的结果是（）
```c
#include <iostream>
using namespace std;

class cla {
	static int n;
public:
	cla() { n++; }
	~cla() { n--; }
	static int get_n() { return n; }
};

int cla::n = 0;

int main()
{
	cla *p = new cla;
	delete p;
	cout << "n=" << cla::get_n() << endl;
	return 0;
}
```

- [ ] A. n=3
- [ ] B. n=4
- [ ] C. n=1
- [x] D. n=0

### 10. 以下程序输出结果是（）
```c
class A
{
public:
	A() :m_iVal(0) { test(); }
	virtual void func() { std::cout << m_iVal << ' '; }
	void test() { func(); }
public:
	int m_iVal;
};

class B : public A
{
public:
	B() { test(); }
	virtual void func()
	{
		++m_iVal;
		std::cout << m_iVal << ' ';
	}
};

int main(int argc, char* argv[])
{
	A* p = new B;
	p->test();
	return 0;
}
```

- [ ] A. 1 0
- [ ] B. 0 1
- [x] C. 0 1 2
- [ ] D. 2 1 0
- [ ] E. 不可预期
- [ ] F. 以上都不对
