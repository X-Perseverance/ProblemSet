### 1. 以下程序的输出结果是（）
```c
int x = 1;
do {
	printf("%2d\n", x++);
}while(x--);
```

- [ ] A. 1
- [ ] B. 无任何输出
- [ ] C. 2
- [x] D. 陷入死循环

### 2. 下面两个结构体在 #pragma pack(4) 和 #pragma pack(8) 的情况下，结构体的大小分别是（）
```c
struct One {
	double d;
	char c;
	int i;
}

struct Two {
	char c;
	double d;
	int i;
}
```

- [ ] A. 16 24，16 24
- [ ] B. 16 20，16 20
- [x] C. 16 16，16 24
- [ ] D. 16 16，24 24

### 3. 下列程序的打印结果是（）
```c
char p1[15]= "abcd", *p2= "ABCD", str[50]= "xyz";
strcpy(str+2, strcat(p1+2,p2+1));
printf("%s", str);
```

- [ ] A. xyabcAB
- [ ] B. abcABz
- [ ] C. ABabcz
- [x] D. xycdBCD
- [ ] E. 运行出错

### 4. 下面程序的输出结果是（）
```c++
#include <iostream>
using namespace std;

void main() {
	int n[][3] = {10, 20, 30, 40, 50, 60};
	int (*p)[3];
	p = n;
	cout << p[0][0] << "," << *(p[0]+1) << "," << (*p)[2] << endl;
}
```

- [ ] A. 10,30,50
- [x] B. 10,20,30
- [ ] C. 20,40,60
- [ ] D. 10,30,60

### 5. 若运行时从键盘上输入9876543210，则下面程序在gcc编译器下的输出结果是（）
```c
int main() {
	int a;
	float b, c;
	scanf("%2d%3f%4f", &a, &b, &c);
	printf("\na=%d,b=%d,c=%f\n", a, b, c);
}
```

- [ ] A. a=98,b=765,c=4321.000000
- [x] B. a=98,b=0,c=0.000000
- [ ] C. a=98,b=765.000000,c=4321.000000
- [ ] D. a=98,b=765.0,c=4321.0

### 6. STL中的unordered_map和priority_queue使用的底层数据结构分别是（）
- [ ] A. rbtree,queue
- [x] B. hashtable,heap
- [ ] C. rbtree,heap
- [ ] D. hashtable,queue

### 7. 下面说法正确的是（）
- [x] A. 一个空类默认一定生成构造函数，拷贝构造函数，赋值操作符，引用操作符，析构函数
- [ ] B. 可以有多个析构函数
- [ ] C. 析构函数可以为virtual，可以被重载
- [ ] D. 类的构造函数如果都不是public访问属性，则类的实例无法创建

> **【分析】**<br>
> &#160; &#160; &#160; &#160; B选项中，析构函数只能有一个；C选项中，由于析构函数没有参数列表，所以不能重载；D选项中，单例模式下，类的构造函数访问属性是private，但仍可创建实例。其目的是保证一个类仅有一个实例，并提供一个访问它的全局访问点，让该实例被所有程序模块共享。<br>

### 8. c++语言中，类ClassA的构造函数和析构函数的执行次数分别为（）
```c++
ClassA *pclassa = new ClassA[5];
delete pclassa;
```

- [x] A. 5,1
- [ ] B. 1,1
- [ ] C. 5,5
- [ ] D. 1,5

### 9. 关于重载和多态正确的是（）
- [ ] A. 如果父类和子类都有相同的方法，参数个数不同，将子类对象赋给父类后，由于子类继承于父类，所以使用父类指针调用父类方法时，实际调用的是子类的方法
- [ ] B. 重载和多态在C++面向对象编程中经常用到的方法，都只在实现子类的方法时才会使用
- [ ] C.
```c++
class A{
void test(float a) {cout<<"1";}
};

class B :public A{
void test(int b) {cout<<"2";}
};

A *a=new A;
B *b=new B;
a=b;
a.test(1.1);
结果是1
```
- [x] D. 选项全部都不正确

### 10. 请选择下列程序的运行结果（）
```c++
#include <iostream>
using namespace std;

class B0
{
public:
	virtual void display()
	{
		cout<<"B0::display0"<<endl;
	}
};
	
class B1 :public B0
{
public:
	void display() { cout<<"B1::display0"<<endl; }
};

class D1 :public B1
{
public:
	void display() { cout<<"D1::display0"<<endl; }
};

void fun(B0 ptr)
{
	ptr.display();
}

int main()
{
	B0 b0;
	B1 b1;
	D1 d1;
	
	fun(b0);
	fun(b1);
	fun(d1);
}
```

- [x] A. B0::display0 B0::display0 B0::display0
- [ ] B. B0::display0 B0::display0 D1::display0
- [ ] C. B0::display0 B1::display0 D1::display0
- [ ] D. B0::display0 B1::display0 B1::display0
