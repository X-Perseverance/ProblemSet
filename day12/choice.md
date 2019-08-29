### 1. 以下不能正确定义二维数组的选项是（）
- [ ] A. int a[2][2] = {{1}, {2}};
- [ ] B. int a[][2] = {1, 2, 3, 4};
- [ ] C. int a[2][2] = {{1}, 2, 3};
- [x] D. int a[2][] = {{1, 2}, {3, 4}};

### 2. 代码生成阶段的主要任务是（）
- [ ] A. 把高级语言翻译成机器语言
- [ ] B. 把高级语言翻译成汇编语言
- [x] C. 把中间代码变换成依赖具体机器的目标代码
- [ ] D. 把汇编语言翻译成机器语言

### 3. 下面程序的输出结果是（）
```c ++
#include <iostream>

void main() {
	int n[][3] = { 10,20,30,40,50,60 };
	int(*p)[3];
	p = n;
	std::cout << p[0][0] << "," << *(p[0] + 1) << "," << (*p)[2] << std::endl;
}
```

- [ ] A. 10,30,60
- [ ] B. 10,30,50
- [x] C. 10,20,30
- [ ] D. 20,40,60

### 4. 下面程序的输出结果是（）
```c ++
#include <iostream>

#define SQR(A) A*A

void main() {
	int x = 6, y = 3, z = 2;
	x /= SQR(y + z) / SQR(y + z);
	std::cout << x << std::endl;
}
```

- [ ] A. 5
- [ ] B. 6
- [ ] C. 1
- [x] D. 0

### 5. 在一个64位的操作系统中定义如下结构体，同时定义如下fool函数，那么fool()程序的执行结果为（）
```c
struct st_task
{
	uint16_t id;
	uint32_t value;
	uint64_t timestamp;
};

void fool()
{
	st_task task = {};
	uint64_t a = 0x00010001;
	memcpy(&task, &a, sizeof(uint64_t));
	printf("%11u,%11u,%11u", task.id, task.value, task.timestamp);
}
```

- [x] A. 1, 0, 0
- [ ] B. 1, 1, 0
- [ ] C. 0, 1, 1
- [ ] D. 0, 0, 1 

> **【解析】**<br>
> ![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/st_task.png)<br>

### 6. STL中的一级容器有（）
- [ ] A. vector, deque, list, set, multiset, map, multimap
- [ ] B. 序列容器, 关联容器, 容器适配器
- [ ] C. set, multiset, map, multimap
- [x] D. vector, deque, list

### 7. 如果有一个类是 myClass , 关于下面代码正确描述的是（）
```c ++
myClass::~myClass() {
	delete this;
	this = NULL;
}
```

- [ ] A. 正确，我们避免了内存泄漏
- [ ] B. 它会导致栈溢出
- [x] C. 无法编译通过
- [ ] D. 这是不正确的，它没有释放任何成员变量

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 在 Myclass 类中，this 的类型为 `Myclass *const this`，它是一个指针常量，也就是说 this 指针本身的内容不能修改，而其指向的内容可以修改。所以，在上述代码中，`this = NULL;` 这条语句会无法通过编译，但若我们去除掉这条语句，上述代码还是有问题的，因为 `delete this;` 会调用析构函数，而析构函数中会再次调用delete this，如此这样循环往复下去，最终会导致栈溢出。<br>

### 8. 如果类 B 继承类 A，A::x() 被声明为虚函数，B::x() 重载了 A::x() 方法，在下述语句中哪个 x() 方法会被调用（）
```c ++
B b;
b.x();
```

- [ ] A. A::x()
- [x] B. B::x()
- [ ] C. A::x() B::x()
- [ ] D. B::x() A::x()

### 9. [函数func的定义如下，那么以下代码在`vs`中输出结果为（）](https://www.nowcoder.com/questionTerminal/9fd169364f4a42599aa7ade7f1c9bbd9)
```c ++
void func(const int& v1, const int& v2)
{
	std::cout << v1 << ' ';
	std::cout << v2 << ' ';
}

int main(int argc, char* argv[])
{
	int i = 0;
	func(++i, i++);
	return 0;
}
```

- [ ] A. 0 1
- [ ] B. 1 2
- [ ] C. 2 1
- [x] D. 2 0
- [ ] E. 程序强制终止并报错
- [ ] F. 结果与编译器有关

> **【切记】**<br>
> &#160; &#160; &#160; &#160; 在C语言中，函数参数入栈顺序为由右向左，但表达式的执行顺序却是未定义的，具体情况和编译器有关。<br>

### 10. 下列一段C++代码的输出是（）
```c ++
#include "stdio.h"

class Base
{
public:
	int Bar(char x)
	{
		return (int)(x);
	}
	virtual int Bar(int x)
	{
		return (2 * x);
	}
};

class Derived : public Base
{
public:
	int Bar(char x)
	{
		return (int)(-x);
	}
	int Bar(int x)
	{
		return (x / 2);
	}
};

int main(void)
{
	Derived Obj;
	Base *pObj = &Obj;
	printf("%d, ", pObj->Bar((char)(100)));
	printf("%d", pObj->Bar(100));
}
```

- [ ] A. 100, -100
- [x] B. 100, 50
- [ ] C. 200, -100
- [ ] D. 200, 50
