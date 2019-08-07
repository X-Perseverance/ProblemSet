### 1. 十进制变量i的值为100，那么八进制的变量i的值为（）
- [ ] A. 146
- [ ] B. 148
- [x] C. 144
- [ ] D. 142

### 2. 有一个如下的结构体，请问在64位编译器下用sizeof(struct A)计算出的大小是多少（）
```c
struct A {
	long a1;
	short a2;
	int a3;
	int *a4;
};
```

- [x] A. 24
- [ ] B. 28
- [ ] C. 16
- [ ] D. 18

### 3. 对于下面的C语言声明描述正确的一项是（）
```c
char (*p)[16];
```

- [ ] A. p是长度为16的字符指针数组
- [ ] B. p是包含16个字符的字符串
- [x] C. p是指向长度为16的字符数组的指针
- [ ] D. p是长度为16的字符数组

### 4. 下面程序运行后的输出结果是（）
```c
#include <stdio.h>

int main() {
	int m = 0123, n = 123;
	printf("%o %o\n", m, n);

	return 0;
}
```

- [ ] A. 0123 0173
- [ ] B. 0123 173
- [x] C. 123 173
- [ ] D. 173 173

### 5. 以下程序运行时，若输入1abcedf2df<回车>输出结果是（）
```c
#include <stdio.h>

int main()
{
	char a = 0, ch;
	while ((ch = getchar()) != '\n')
	{
		if (a % 2 != 0 && (ch >= 'a' && ch <= 'z'))
			ch = ch - 'a' + 'A';
		a++;
		putchar(ch);
	}
	printf("\n");
}
```

- [ ] A. 1abcedf2df
- [ ] B. 1ABCEDF2DF
- [x] C. 1AbCeDf2dF
- [ ] D. 1abceDF2DF

### 6. 关于内联函数说法错误的是（）
- [ ] A. 不是任何一个函数都可定义成内联函数
- [ ] B. 内联函数的函数体内不能含有复杂的结构控制语句
- [x] C. 递归函数可以被用来作为内联函数
- [ ] D. 内联函数一般适合于只有1~5行语句的小函数

### 7. 关于“深拷贝”，下列说法正确的是（）
- [x] A. 会拷贝成员数据的值和会拷贝静态分配的成员对象
- [ ] B. 只会拷贝成员数据的值
- [ ] C. 只会拷贝静态分配的成员对象
- [ ] D. 只会拷贝动态分配的成员对象

### 8. 若要对data类中重载的加法运算符成员函数进行声明，下列选项中正确的是（）
- [x] A. Data operator+(Data);
- [ ] B. Data operator(Data);
- [ ] C. operator+(Data,Data);
- [ ] D. Data+(Data);

### 9. 下面程序运行结果为（）
```c++
#include <iostream>

using namespace std;

char fun(char x, char y) {
	if (x < y)
		return x;
	return y;
}

int main() {
	int a = '1', b = '1', c = '2';
	cout << fun(fun(a, b), fun(b, c));

	return 0;
}
```

- [ ] A. 运行出错
- [ ] B. 2
- [ ] C. 3
- [x] D. 1

### 10. 下面程序运行结果是（）
```c++
#include <iostream>

using namespace std;

int f(int n) {
	if (n == 1)
		return 1;
	else
		return (f(n - 1) + n * n * n);
}

int main() {
	int s = f(3);
	cout << s << endl;

	return 0;
}
```

- [ ] A. 8
- [ ] B. 9
- [ ] C. 27
- [x] D. 36
