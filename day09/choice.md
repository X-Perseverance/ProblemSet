### 1. 32位系统中，定义**a[3][4]，则变量占用内存空间为（）
- [ ] A. 4
- [x] B. 48
- [ ] C. 192
- [ ] D. 12

### 2. 二维数组 X 按行顺序存储，其中每个元素占1个存储单元。若X[4][4]的存储地址为Oxf8b82140，X[9][9]的存储地址为Oxf8b8221c，则X[7][7]的存储地址为（）
- [x] A. Oxf8b821c4
- [ ] B. Oxf8b821a6
- [ ] C. Oxf8b82198
- [ ] D. Oxf8b821c0

### 3. 若输入x=9999，求函数返回值（）
```c
int func(int x) {
	int count = 0;
	while (x)
	{
		count++;
		x = x & (x - 1);
	}
	return count;
}
```

- [x] A. 8
- [ ] B. 9
- [ ] C. 10
- [ ] D. 12

### 4. 根据下面递归函数：调用函数Fun(2)，返回值是多少（）
```c
int Fun(int n)
{
	if (n == 5)
		return 2;
	else
		return 2 * Fun(n + 1);
}
```

- [ ] A. 2
- [ ] B. 4
- [ ] C. 8
- [x] D. 16

### 5. 执行下面语句后的输出为（）
```c
int I = 1;
if (I <= 0)
	printf("****\n");
else
	printf("%%%%\n");
```

- [x] A. %%
- [ ] B. ****
- [ ] C. 有语法错，不能正确执行
- [ ] D. %%%%

### 6. [在C++，下列哪一个可以做为对象继承之间的转换（）](https://www.nowcoder.com/questionTerminal/a00aa56e4819416f88e7b13a86df6e3a)
- [x] A. static_cast
- [ ] B. reinterpret_cast
- [x] C. dynamic_cast
- [ ] D. const_cast

### 7. 类模板的使用实际上是类模板实例化成一个具体的（）
- [x] A. 类
- [ ] B. 函数
- [ ] C. 模板类
- [ ] D. 对象

### 8. 有如下C++代码，那么 `A *p=new B; p->foo(); p->bar();` 输出为（）
```c ++
struct A {
	void foo() { printf("foo"); }
	virtual void bar() { printf("bar"); }
	A() { bar(); }
};
struct B :A {
	void foo() { printf("b_foo"); }
	void bar() { printf("b_bar"); }
};
```

- [x] A. barfoob_bar
- [ ] B. foobarb_bar
- [ ] C. barfoob_foo
- [ ] D. foobarb_fpp

### 9. 下面的程序输出可能是什么（）
```c ++
class Printer {
public:
	Printer(std::string name) { std::cout << name; }
};

class Container {
public:
	Container() : b("b"), a("a") {}
	Printer a;
	Printer b;
};

int main() {
	Container c;
	return 0;
}
```

- [ ] A. 可能是 "ab" 或 "ba"，依赖于具体的实现
- [ ] B. 一直都是 "ba"
- [x] C. 一直都是 "ab"

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 由于成员变量在类中的声明次序就是其在初始化列表中的初始化顺序，所以先初始化a，再初始化b。

### 10. 下面代码可以通过编译吗？如果不能应该如何修改？（）
```c ++
template<class T>
class Foo {
	T tVar;
public:
	Foo(T t) : tVar(t) {}
};

template<class T>
class FooDerived :public Foo<T> {
};

int main()
{
	FooDerived<int> d(5);
	return 0;
}
```

- [ ] A. 代码可以正确通过编译
- [ ] B. 编译错误，FooDerived是一个继承模板类的非模板类，它的类型不能改变
- [ ] C. 编译错误，tVal变量是一个不确定的类型
- [x] D. 编译错误，可以在FooDerived类中添加一个构造函数解决问题
