### 1. 在嵌套使用if语句时，C语言规定else总是（）
- [ ] A. 和之前与其具有相同缩进位置的if配对
- [ ] B. 和之前与其最近的if配对
- [x] C. 和之前与其最近的且不带else的if配对
- [ ] D. 和之前的第一个if配对

### 2. 以下系统中，int类型占几个字节，指针占几个字节，操作系统可以使用的最大内存空间是多大（）
- [ ] A. 32位下：4, 4, 2^32&#160; &#160; &#160; 64位下：8, 8, 2^64
- [ ] B. 32位下：4, 4, 不限制&#160; &#160; 64位下：4, 8, 不限制
- [x] C. 32位下：4, 4, 2^32&#160; &#160; &#160; 64位下：4, 8, 2^64
- [ ] D. 32位下：4, 4, 2^32&#160; &#160; &#160; 64位下：4, 4, 2^64

### 3. 以下程序的输出结果是（）
```c
#include <stdio.h>

int main()
{
	int i, a[10];
	for (i = 9; i >= 0; i--) 
		a[i] = 10 - i;
	printf("%d%d%d", a[2], a[5], a[8]);

	return 0;
}
```

- [ ] A. 258
- [ ] B. 741
- [x] C. 852
- [ ] D. 369

### 4. 下面C程序的输出结果为（）
```c
int i = 0, a = 1, b = 2, c = 3;
i = ++a || ++b || ++c;
printf("%d %d %d %d", i, a, b, c);
```

- [x] A. 1 2 2 3
- [ ] B. 1 2 3 4
- [ ] C. 3 2 3 4
- [ ] D. 3 3 3 4

### 5. [下面代码不能正确输出hello的选项为（）](https://www.nowcoder.com/questionTerminal/4a4c163af45540a5a39d20db413af1e6?source=relative)
```c
#include <stdio.h>

struct str_t {
	long long len;
	char data[32];
};

struct data1_t {
	long long len;
	int data[2];
};

struct data2_t {
	long long len;
	char *data[1];
};

struct data3_t {
	long long len;
	void *data[];
};

int main(void)
{
	struct str_t str;
	memset((void*)&str, 0, sizeof(struct str_t));
	str.len = sizeof(struct str_t) - sizeof(int);
	snprintf(str.data, str.len, "hello"); //VS下为_snprintf
	____________________________________;
	____________________________________;
	return 0;
}
```

- [ ] A. struct data3_t *pData=(struct data3_t*)&str;&#160; &#160; printf("data:%s%s\n",str.data,(char*)(&(pData->data[0])));
- [x] B. struct data2_t *pData=(struct data2_t*)&str;&#160; &#160; printf("data:%s%s\n",str.data,(char*)(pData->data[0]));
- [ ] C. struct data1_t *pData=(struct data1_t*)&str;&#160; &#160; printf("data:%s%s\n",str.data,(char*)(pData->data));
- [ ] D. struct str_t *pData=(struct str_t*)&str;&#160; &#160; printf("data:%s%s\n",str.data,(char*)(pData->data));

### 6. 哪个操作符不能被重载（）
- [ ] A. `,` (逗号)
- [ ] B. `()`
- [x] C. `.` (点)
- [ ] D. `[]`
- [ ] E. `->`

### 7. 下列对重载函数的描述中，（）是错误的。
- [x] A. 重载函数中不允许使用默认参数
- [ ] B. 重载函数中编译时根据参数表进行选择
- [ ] C. 构造函数重载将会给初始化带来多种方式
- [ ] D. 不要使用重载函数来描述毫无相干的函数

### 8. 下列关于多态性说法不正确的是（）
- [ ] A. 多态性是指同名函数对应多种不同的实现
- [x] B. 重载方式仅有函数重载
- [ ] C. 重载方式包含函数重载和运算符重载
- [ ] D. 多态性表现为静态和动态两种方式

### 9. 分析一下这段程序的输出（）
```c ++
#include <iostream>
using namespace std;

class B {
public:
	B() {
		cout << "default constructor" << " ";
	}
	~B() {
		cout << "destructed" << " ";
	}
	B(int i) : data(i) {
		cout << "constructed by parameter" << data << " ";
	}

private:
	int data;
};

B Play(B b) {
	return b;
}

int main(int argc, char *argv[])
{
	B temp = Play(5);
	return 0;
}
```

- [x] A. constructed by parameter5 destructed destructed
- [ ] B. constructed by parameter5 destructed
- [ ] C. default constructor" constructed by parameter5 destructed
- [ ] D. default constructor" constructed by parameter5 destructed destructed

### 10. 求输出结果（）
```c ++
#include <iostream>
using namespace std;

class A {
public:
	virtual void print() {
		cout << "A::print()" << "\n";
	}
};

class B : public A {
public:
	virtual void print() {
		cout << "B::print()" << "\n";
	}
};

class C : public A {
public:
	virtual void print() {
		cout << "C::print()" << "\n";
	}
};

void print(A a) {
	a.print();
}

int main()
{
	A a, *aa, *ab, *ac;
	B b;
	C c;
	aa = &a;
	ab = &b;
	ac = &c;
	a.print();
	b.print();
	c.print();
	aa->print();
	ab->print();
	ac->print();
	print(a);
	print(b);
	print(c);
}
```

- [ ] A. C::print() B::print() A::print() A::print() B::print() C::print() A::print() A::print() A::print()
- [x] B. A::print() B::print() C::print() A::print() B::print() C::print() A::print() A::print() A::print()
- [ ] C. A::print() B::print() C::print() A::print() B::print() C::print() B::print() B::print() B::print()
- [ ] D. C::print() B::print() A::print() A::print() B::print() C::print() C::print() C::print() C::print()
