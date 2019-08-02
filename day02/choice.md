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
> ![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/bitfield.png)<br>
> &#160; &#160; &#160; &#160; 所以该结构体位段部分共占12个字节，再加上最后一个变量 index 的空间大小1字节，即13个字节。但是，根据结构体的内存对齐规则可知，结构体总大小为最大对齐数的整数倍，在这里最大对齐数为4，所以最终的结果应为16字节。<br>

### 6.以下关于C++的描述中（）是正确的
- [ ] A. 任何指针都必须指向一个实例
- [ ] B. 子类指针不可以指向父类实例
- [x] C. 任何引用都必须指向一个实例
- [ ] D. 引用所指向的实例不可能无效

### 7. 以下不是 `double compare(int,int)` 的重载函数的是()
- [ ] A. int compare(double,double)
- [ ] B. double compare(double,double)
- [ ] C. double compare(double,int)
- [x] D. int compare(int,int)

### 8. 关于虚函数的描述正确的是()
- [ ] A. 派生类的虚函数与基类的虚函数具有不同的参数个数和类型
- [x] B. 内联函数不能是虚函数
- [ ] C. 派生类必须重新定义基类的虚函数
- [ ] D. 虚函数可以是一个static型的函数

### 9. 请将下列构造函数补充完整，使得程序的运行结果是5
```c++
#include <iostream>

using namespace std;

class Sample {
public:
	Sample(int x) {
		________
	}
	~Sample() {
		if(p) delete p;
	}
	int show() {
		return *p;
	}
	
private:
	int*p;
};

int main() {
	Sample S(5);
	cout << S.show() << endl;
	
	return 0;
}
```

- [ ] A. `*p=x;`
- [x] B. `p=new int(x);`
- [ ] C. `*p=new int(x);`
- [ ] D. `p=&x;`

### 10. 关于c++的inline关键字，以下说法正确的是()
- [ ] A. 使用inline关键字的函数会被编译器在调用处展开
- [ ] B. 头文件中可以包含inline函数的声明
- [ ] C. 可以在同一个项目的不同源文件内定义函数名相同但实现不同的inline函数
- [x] D. 定义在Class声明内的成员函数默认是inline函数
- [ ] E. 优先使用Class声明内定义的inline函数
- [ ] F. 优先使用Class实现的内inline函数的实现
