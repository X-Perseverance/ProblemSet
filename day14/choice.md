### 1. 定义 `char dog[] = "wang\0miao";` 那么 sizeof(dog) 与 strlen(dog) 分别是多少（）
- [x] A. 10,4
- [ ] B. 4,4
- [ ] C. 9,9
- [ ] D. 9,4

### 2. 假设寄存器为8位，用补码形式存储机器数，包括一位符号位，那么十进制数 -25 在寄存器表示为（）
- [ ] A. 67H
- [ ] B. 99H
- [ ] C. E6H
- [x] D. E7H

### 3. 下面代码的执行结果是什么（）
```c ++
char ccString1[] = "Is Page Fault??";
char ccString2[] = "No Page Fault??";

strcpy(ccString1, "No");

if (strcmp(ccString1, ccString2) == 0)
	cout << ccString2;
else
	cout << ccString1;
```

- [x] A. No
- [ ] B. No Page Fault??
- [ ] C. Is Page Fault??
- [ ] D. 其他三项都错

### 4. [输入参数为 197 时，函数返回多少（）](https://www.nowcoder.com/questionTerminal/618c7143cc664cd4afe8ddb2ccaab2cf?from=14pdf)
```c
int Function(unsigned int n) {
	n = (n & 0x55555555) + ((n >> 1) & 0x55555555);
	n = (n & 0x33333333) + ((n >> 2) & 0x33333333);
	n = (n & 0x0f0f0f0f) + ((n >> 4) & 0x0f0f0f0f);
	n = (n & 0x00ff00ff) + ((n >> 8) & 0x00ff00ff);
	n = (n & 0x0000ffff) + ((n >> 16) & 0x0000ffff);

	return n;
}
```

- [ ] A. 2
- [ ] B. 3
- [x] C. 4
- [ ] D. 5

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 采用平行算法求二进制数中 1 的个数。<br>

### 5. 下面程序的功能是输出数组的全排列，请填空（）
```c ++
void perm(int list[], int k, int m)
{
	if (_____)
	{
		copy(list, list + m, ostream_iterator<int>(cout, " "));
		cout << endl;
		return;
	}
	for (int i = k; i <= m; i++)
	{
		swap(&list[k], &list[i]);
		_____;
		swap(&list[k], &list[i]);
	}
}
```

- [ ] A. k!=m 和 perm(list, k+1, m)
- [x] B. k==m 和 perm(list, k+1, m)
- [ ] C. k!=m 和 perm(list, k, m)
- [ ] D. k==m 和 perm(list, k, m)

### 6. C++中以下关于函数调用的说法哪个是正确的（）
- [ ] A. 传地址后实参和形参指向不同的对象
- [ ] B. 传引用后实参和形参是不同的对象
- [ ] C. 传值后对形参的修改会改变实参的值
- [x] D. 其他三项都不对

### 7. 有一个类 B 继承自类 A，他们数据成员如下，则构造函数中，成员变量一定要通过初始化列表来初始化的是（）
```c ++
class A {
	...
private:
	int a;
};

class B : public A {
	...
private:
	int a;
public:
	const int b;
	A &c;
	static const char* d;
	B* e;
};
```

- [ ] A. a b c
- [ ] B. b c e
- [ ] C. b c d e
- [ ] D. c e
- [ ] E. b d
- [x] F. b c

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 类中包含以下成员，必须放在初始化列表位置进行初始化：（1）引用成员变量；（2）const成员变量；（3）类类型成员(该类没有默认构造函数)。<br>

### 8. [以下代码编译有错误，哪个选项能解决编译错误（）](https://www.nowcoder.com/questionTerminal/5eb3f563ef0149fc81c6e085e12bed86?toCommentId=109576)
```c ++
class A {
public:
	int GetValue() const {
		vv = 1;
		return vv;
	}
private:
	int vv;
};
```

- [ ] A. 改变成员变量 vv 为 `mutable int vv`
- [ ] B. 改变成员函数 GetValue 的声明，以使其不是const的
- [ ] C. 都不能修复编译错误
- [x] D. 都可以修复编译错误

> **【解析】**<br>
> &#160; &#160; &#160; &#160; mutable的中文意思是“可变的，易变的”，和constant（即C++中的const）是反义词。 在C++中，mutable也是为了突破const的限制而设置的，被mutable修饰的变量，将永远处于可变的状态，即使在一个const函数中。<br>

### 9. 下面程序运行后的结果为（）
```c
char str[] = "glad to test something";
char *p = str;
p++;
int *p1 = reinterpret_cast<int *>(p);
p1++;
p = reinterpret_cast<char *>(p1);
printf("result is %s\n", p);
```

- [ ] A. result is glad to test something
- [ ] B. result is ad to test something
- [ ] C. result is test something
- [x] D. result is to test something

### 10. 以下程序的输出是（）
```c ++
class Base {
public:
	Base(int j) : i(j) {}
	virtual~Base() {}
	void func1() {
		i *= 10;
		func2();
	}
	int getValue() {
		return i;
	}
protected:
	virtual void func2() {
		i++;
	}
protected:
	int i;
};

class Child : public Base {
public:
	Child(int j) : Base(j) {}
	void func1() {
		i *= 100;
		func2();
	}
protected:
	void func2() {
		i += 2;
	}
};

int main() {
	Base * pb = new Child(1);
	pb->func1();
	cout << pb->getValue() << endl;
	delete pb;
}
```

- [ ] A. 11
- [ ] B. 101
- [x] C. 12
- [ ] D. 102
