### 1. 请声明一个指针，其所指向的内存地址不能改变，但内存中的值可以被改变（）
- [ ] A. const int const *x = &y;
- [x] B. int * const x = &y;
- [ ] C. const int *x = &y;
- [ ] D. int const *x = &y;
- [ ] E. const int * const x = &y;

### 2. 以下说法中正确的是（）
- [ ] A. C++程序中的main()函数必须放在程序的开始部分
- [x] B. C++程序的入口函数是main函数
- [ ] C. 在C++程序中，要调用的函数必须在main()函数中

### 3. 下面哪个指针表达式可以用来引用数组元素 a[i][j][k][l]（）
- [ ] A. (((a+i)+j)+k)+l)
- [x] B. \*(\*(\*(\*(a+i)+j)+k)+l)
- [ ] C. (((a+i)+j)+k+l)
- [ ] D. ((a+i)+j+k+l)

### 4. fun(21)的运行结果是（）
```c
int fun(int a) {
	a ^= (1 << 5) - 1;
	return a;
}
```

- [x] A. 10
- [ ] B. 5
- [ ] C. 3
- [ ] D. 8

### 5. 以下程序的输出结果是（）
```c ++
#include <iostream>
using namespace std;

void func(char **m) {
	++m;
	cout << *m << endl;
}

int main() {
	static char *a[] = { "morning", "afternoon", "evening" };
	char **p;
	p = a;
	func(p);
	return 0;
}
```

- [x] A. afternoon
- [ ] B. 字符o的起始地址
- [ ] C. 字符o
- [ ] D. 字符a的起始地址

### 6. 下面对析构函数的正确描述是（）
- [ ] A. 系统不能提供默认的析构函数
- [ ] B. 析构函数必须由用户定义
- [x] C. 析构函数没有参数
- [ ] D. 析构函数可以设置默认参数

### 7. 某函数申明如：`void Func(int &nVal1);` 有 int a，下面使用正确的为（）
- [x] A. Func(a)
- [ ] B. Func(&a)
- [ ] C. Func(*a)
- [ ] D. Func(&(*a))

### 8. 当一个类的某个函数被说明为 virtual，则在该类的所有派生类中的同原型函数（）
- [ ] A. 只有被重新说明时才识虚函数
- [ ] B. 只有被重新说明为virtual时才是虚函数
- [ ] C. 都不是虚函数
- [x] D. 都是虚函数

### 9. 有如下程序，运行时的输出结果是（）
```c ++
#include <iostream>
using namespace std;

class MyClass {
public:
	MyClass(int i = 0) { cout << 1; }
	MyClass(const MyClass& x) { cout << 2; }
	MyClass& operator=(const MyClass& x) { cout << 3; return*this; }
	~MyClass() { cout << 4; }
};

int main() {
	MyClass obj1(1), obj2(2), obj3(obj1);
	return 0;
}
```

- [ ] A. 121,444
- [x] B. 112,444
- [ ] C. 11,114,444
- [ ] D. 11,314,445
- [ ] E. 11,314,444

### 10. 代码执行后，a和b的值分别为（）
```c ++
class Test {
public:
	int a;
	int b;
	virtual void fun() {}
	Test(int temp1 = 0, int temp2 = 0)
	{
		a = temp1;
		b = temp2;
	}
	int getA()
	{
		return a;
	}
	int getB()
	{
		return b;
	}
};

int main()
{
	Test obj(5, 10);
	// Changing a and b
	int* pInt = (int*)&obj;
	*(pInt + 0) = 100;
	*(pInt + 1) = 200;
	cout << "a = " << obj.getA() << endl;
	cout << "b = " << obj.getB() << endl;
	return 0;
}
```

- [x] A. 200 10
- [ ] B. 5 10
- [ ] C. 100 200
- [ ] D. 100 10

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 由于在Test类中含有一个虚函数 fun ，那么其实例化对象 obj 在内存分布中先使用4字节存放虚函数表指针，再依次存放成员变量a和b，所以程序中 `*(pInt + 0) = 100;` 改变的是虚表指针的内容，`*(pInt + 1) = 200;` 改变的是a的值，而b并没有改变，故而答案选A。
