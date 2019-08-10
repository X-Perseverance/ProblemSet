### 1. 在`int p[][4]={{1}, {3,2}, {4,5,6}, {0}};`中，p[1][2]的值是（）
- [ ] A. 1
- [x] B. 0
- [ ] C. 6
- [ ] D. 2

### 2. 下列关于对象数组的描述中，（）是错误的
- [x] A. 对象数组只能赋初值而不能再赋值
- [ ] B. 对象数组的每个元素是同一个类的对象
- [ ] C. 对象数组的数组名是一个指针常量
- [ ] D. 对象数组的下标是从0开始的

### 3. 设变量已正确定义，以下不能统计出一行中输入字符个数（不包含回车符）的程序段是（）
- [ ] A. `n=0; while(ch=getchar()!='\n') n++;`
- [ ] B. `n=0; while(getchar()!='\n') n++;`
- [ ] C. `for(n=0; getchar()!='\n'; n++);`
- [x] D. `n=0; for(ch=getchar(); ch!='\n'; n++);`

### 4. 下列程序段执行后，输出d的值为（）
```c
void main()
{
	int a=1, b=0, c=-1, d=0;
	d = ++a||++b&&++c;
	cout << d << endl;
}
```

- [x] A. 1
- [ ] B. 2
- [ ] C. 3
- [ ] D. 0

### 5. 下面程序输出是什么（）
```c
#include <stdio.h>

int main()
{
	int a=1, b=2, c=3, d=0;
	if(a == 1 && b++==2)
		if(b!=2||c--!=3)
			printf("%d,%d,%d\n", a, b, c);
		else
			printf("%d,%d,%d\n", a, b, c);
	else
		printf("%d,%d,%d\n", a, b, c);
	return 0;
}
```

- [ ] A. 1，2，3
- [ ] B. 1，3，2
- [ ] C. 3，2，1
- [x] D. 1，3，3

### 6. 下面关于类定义的说法中，正确的是（）
- [x] A. 类定义中包括数据成员和函数成员的声明
- [ ] B. 类成员的缺省访问权限是保护的
- [ ] C. 数据成员必须被声明为私有的
- [ ] D. 成员函数只能在类体外进行定义

### 7. 有如下类模板定义，已知b1 b2是BigNumber的两个对象，则下列表达式中错误的是（）
```c ++
template<class T> 
class BigNumber {
	long　n;
public:
	BigNumber(T i):n(i) {}
	BigNumber operator+(BigNumber b) {
		return　BigNumber(n+b.n);
	}
};
```

- [ ] A. 3+3
- [ ] B. b1+3
- [ ] C. b1+b2
- [x] D. 3+b1

### 8. 假定一个类的构造函数为`A(int aa, int bb){a=aa--; b=a*bb;}`，则执行`A x(4,5);`语句后，x.a和x.b的值分别为（）
- [ ] A. 20和5
- [ ] B. 3和15
- [ ] C. 5和4
- [x] D. 4和20

### 9. 代码运行结果是（）
```c ++
#include <iostream>
#include <string>

using namespace std;

class A {
	friend long fun(A s) {
		if (s.x<3) {
			return 1;
		}
		return s.x+fun(A(s.x - 1));
	}
public:
	A(long a) {
		x = a--;
	}
private:
	long x;
};

int main() {
	int sum=0;
	for(int i=0; i<5; i++){
		sum += fun(A(i));
	}
	cout << sum;
	return 0;
}
```

- [ ] A. 21
- [x] B. 15
- [ ] C. 9
- [ ] D. 36

### 10. 下面程序的输出是什么（）
```c ++
#include <iostream>

using namespace std;

class parent {
	int i;
protected:
	int x;
public:
	parent() {x=0; i=0;}
	void change() {x++; i++;}
	void display();
};

class son :public parent {
public:
	void modify();
};

void parent::display() {cout<<"x="<<x<<endl;}
void son::modify() {x++;}

int main() {
	son A; parent B;
	A.display();
	A.change();
	A.modify();
	A.display();
	B.change();
	B.display();
}
```

- [ ] A. x=1 x=0 x=2
- [ ] B. x=2 x=0 x=1
- [x] C. x=0 x=2 x=1
- [ ] D. x=0 x=1 x=2
