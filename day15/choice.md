### 1. 如下所示对两个字符 a 和 b 进行初始化， 则下面叙述中正确的是（）
```c
char a[] = "ABCDEF";
char b[] = {'A','B','C','D','E','F'};
```

- [x] A. a 数组比 b 数组长度长
- [ ] B. a 与 b 长度相同
- [ ] C. a 与 b 数组完全相同
- [ ] D. a 和 b 中都存放字符串

### 2. x 是一个行列数均为1000的二维数组，下面代码效率执行最高的是（）
- [ ] A. for (int j = 0; j < 1000; j++) for (int i = 0; i < 1000; i++) x[i][j] += x[j][i];
- [ ] B. for (int i = 0; i < 1000; j++) for (int j = 0; j < 1000; j++) x[i][j] += x[j][i];
- [ ] C. for (int i = 0; i < 1000; j++) for (int j = 0; j < 1000; j++) x[j][i] += x[j][i];
- [x] D. for (int i = 0; i < 1000; i++) for (int j = 0; j < 1000; j++) x[i][j] += x[i][j];

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 本题主要考察了CPU cache的预取操作，由于数组x[1000][1000]在内存中是按行进行存储，所以按行访问效率会更高。D选项外部循环是按行进行，因此操作第 i 行时，会将第 i 行后面的部分数据预取到 cache 中，这样就加快了代码的执行速率，而ABC选项中都有跳行的操作，不能发挥 cache 的预取操作功能。<br>

### 3. C++中关于堆和栈的说法，哪个是错误的（）
- [ ] A. 堆的大小仅受操作系统的限制，栈的大小一般一般较小
- [ ] B. 在堆上频繁的调用new/delete容易产生内存碎片，栈没有这个问题
- [x] C. 堆和栈都可以静态分配
- [ ] D. 堆和栈都可以动态分配

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 在实际编程中，我们会经常用到一些数组，但在很多情况下，我们并不能确定这些数组应该使用多大的空间，所以一般我们会将这些数组定义的足够大，但若因为某种原因数组的空间利用率有增加或者减少，这时我们又必须重新去修改程序，扩大或缩小数组的存储空间。上述这种分配固定大小内存的分配方法称为**静态内存分配**，可见这种方法有一些严重的缺陷。<br>
> &#160; &#160; &#160; &#160; 为了解决上述问题，我们可以采用动态内存分配的方法。所谓的**动态内存分配**就是指在程序执行的过程中动态地分配或者回收存储空间的方法，动态内存分配不像数组等静态内存分配方法那样需要预先分配存储空间，而是由系统根据程序的需要即时分配，且分配的大小就是程序要求的大小。<br>
> &#160; &#160; &#160; &#160; 总的来说，内存的静态分配和动态分配有以下两个方面的区别：<br>
> &#160; &#160; &#160; &#160; （1）时间不同<br>
> &#160; &#160; &#160; &#160; 静态分配发生在程序编译和链接的时候，动态分配则发生在程序调入和执行的时候。<br>
> &#160; &#160; &#160; &#160; （2）空间不同<br>
> &#160; &#160; &#160; &#160; 堆都是动态分配的，没有静态分配的堆；<br>
> &#160; &#160; &#160; &#160; 栈有两种分配方式：静态分配和动态分配。静态分配由编译器完成，比如局部变量的分配。动态分配由函数 alloca() 进行分配，并且编译器会自动释放，无需我们手工释放。<br>

### 4. 下面程序会输出什么（）
```c
static int a = 1;
void fun1(void) { a = 2; }
void fun2(void) { int a = 3; }
void fun3(void) { static int a = 4; }

int main(int argc, char** args) {
	printf(“%d”, a);
	fun1();
	printf(“%d”, a);
	fun2();
	printf(“%d”，a);
	fun3();
	printf(“%d”, a);
}
```

- [ ] A. 1 2 3 4
- [x] B. 1 2 2 2
- [ ] C. 1 2 2 4
- [ ] D. 1 1 1 4

### 5. [在 main() 函数中，调用 ModifyString(text) 之后， text 的值是多少（）](https://www.nowcoder.com/questionTerminal/b9a49e1702c4422c9b5ef0b11509bb62)
```c
int FindSubString(char* pch)
{
	int count = 0;
	char * p1 = pch;
	while (*p1 != '\0')
	{
		if (*p1 == p1[1] - 1)
		{
			p1++;
			count++;
		}
		else
			break;
	}
	
	int count2 = count;
	while (*p1 != '\0')
	{
		if (*p1 == p1[1] + 1)
		{
			p1++;
			count2--;
		}
		else
			break;
	}
	
	if (count2 == 0)
		return count;
	return 0;
}

void ModifyString(char* pText)
{
	char * p1 = pText;
	char * p2 = p1;
	while (*p1 != '\0')
	{
		int count = FindSubString(p1);
		if (count > 0)
		{
			*p2++ = *p1;
			sprintf(p2, "%i", count);
			while (*p2 != '\0')
				p2++;
			p1 += count + count + 1;
		}
		else
			*p2++ = *p1++;
	}
}

void main()
{
	char text[32] = "XYBCDCBABABA";
	ModifyString(text);
	printf(text);
}
```

- [ ] A. XYBCDCBABABA
- [ ] B. XYBCBCDA1BAA
- [x] C. XYBCDCBA1BAA
- [ ] D. XYBCDDBA1BAB

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 首先分析一下 FindSubString() 函数的作用：该函数就是要从一个字符串中找到一个回文子串，这个回文子串中的字符的ASCII码值是按递增再递减的顺序排列且是相邻递增或递减，比如字符串 "ABCBA" 就是一个符合要求的回文子串，而 "ABCB" 、 "BCBA" 以及 "ABDBA" 都不符合要求。若找到了符合要求的子串，那么该函数会返回这个子串长度的一半值，否则返回0。<br>
> &#160; &#160; &#160; &#160; 对上述程序来说，给定的字符串是 "XYBCDCBABABA"，那么该字符串中第一个符合要求的回文子串就是 "ABA"，在这里，有人可能会有疑问，为什么不是 "BCDCB" 呢？我们将代码和程序结合起来再看看，会发现：当程序遍历到这个子串的最后一个 'B' 时，后面的 'A' 也会遍历到，此时 count2 变为 -1，函数 FindSubString() 将返回 0，所以严格意义上来说，并没有 "BCDCB" 这个回文子串，而是有 "BCDCBA" 这个普通子串。继续刚才的子串 "ABA"，那么该函数将会返回 1。<br>
> &#160; &#160; &#160; &#160; 接着再来分析 ModifyString() 函数的作用： 先第一次进入 `while(*p1 != '\0')` 循环，当函数 FindSubString() 找到了第一个回文子串 "ABA" 并返回了 1 后，此时 p1 和 p2 都指向第一个 'A'；执行 `*p2++ = *p1;` 后，p1 不变，而 p2 指向 'B'；接着执行 `sprintf(p2, "%i", count);`，此时 `ABA` 变为 `A1'\0'`，其中 '\0' 是函数 sprintf() 自动添加的；再经过 `while(*p2 != '\0')` 循环之后，p2 指向 '\0'；再经过 `p1 += count + count + 1` 之后，p1 指向 '\0' 后面的B，也就是原字符串中倒数第一个B，此时原字符串已经变为 "XYBCDCBA1'\0'BA"。当第二次进入 `while(*p1 != '\0')` 循环后，只能执行 `else` 部分的命令，原字符串依次变为 "XYBCDCBA1BBA" 、 "XYBCDCBA1BAA"。所以程序执行完之后，text 的最终结果为 "XYBCDCBA1BAA"，即选项C。<br>

### 6. 所谓数据封装就是将一组数据和与这组数据有关操作组装在一起形成一个集合，这集合也就是（）
- [x] A. 类
- [ ] B. 对象
- [ ] C. 函数体
- [ ] D. 数据块

### 7. [关于以下代码，哪个说法是正确的（）](https://www.nowcoder.com/questionTerminal/45bb35c18c434829af740c0d843fcb1e)
```c ++
myClass::foo() {
	delete this;
}
...
void func() {
	myClass *a = new myClass();
	a->foo();
}
```

- [ ] A. 它会引起栈溢出
- [x] B. 都不正确
- [ ] C. 它不能编译
- [ ] D. 它会引起段错误

> **【解析】**<br>
> &#160; &#160; &#160; &#160; delete this（对象请求自杀）是允许的，但是必须保证：<br>
> &#160; &#160; &#160; &#160; （1）该this对象是百分百new出来的，并且是最普通的new出来的，不能是new[]，定位new等等；<br>
> &#160; &#160; &#160; &#160; （2）该成员函数是this对象最后调用的成员函数（因为成员函数第一个参数是隐藏的this指针）；<br>
> &#160; &#160; &#160; &#160; （3）delete this 之后不能访问到成员变量和虚函数；<br>
> &#160; &#160; &#160; &#160; （4）delete this 不能放在析构函数中，否则无限递归，从而造成堆栈溢出。<br>

### 8. 假定 CSomething 是一个类，执行下面这些语句之后，内存里创建了（）个 CSomething 对象。
```c ++
CSomething a();
CSomething b(2);
CSomething c[3];
CSomething &ra = b;
CSomething d = b;
CSomething *pA = c;
CSomething *p = new CSomething(4);
```

- [ ] A. 10
- [ ] B. 9
- [ ] C. 8
- [ ] D. 7
- [x] E. 6
- [ ] F. 5

> **【解析】**<br>
> ```c ++
> CSomething a(); //声明一个函数a，函数参数为空，返回值类型为CSomething
> CSomething b(2); //调用带参构造函数，创建了对象b   +1
> CSomething c[3]; //调用无参构造函数，创建一个含有三个对象的数组c   +3
> CSomething &ra = b; //引用对象b，没有创建新对象
> CSomething d = b; //调用拷贝构造函数，创建了对象d   +1
> CSomething *pA = c; //将对象c赋给对象指针pA，使pA指向对象c，没有创建新对象
> CSomething *p = new CSomething(4); //通过new创建了新对象   +1
> ```

### 9. [下面这段代码运行时会出现什么问题（）](https://www.nowcoder.com/questionTerminal/98cb416bbc794149884737669a3c1ac4)
```c++
class A {
public:
	void f() {
		printf("A\n");
	}
};

class B : public A {
public:
	virtual void f() {
		printf("B\n");
	}
};

int main()
{
	A *a = new B;
	a->f();
	delete a;

	return 0;
}
```

- [ ] A. 没有问题，输出B
- [x] B. 不符合预期的输出A
- [ ] C. 程序不正确
- [ ] D. 以上答案都不正确

> **【解析】**<br>
> &#160; &#160; &#160; &#160; 执行 `a->f();` 这条语句会输出 A，接着执行 `delete a;` 这条语句会导致程序崩溃。<br>

### 10. [下面这段代码会打印出什么（）](https://www.nowcoder.com/questionTerminal/c0dd84ffdcd14c57a17696bf5c0f819f?toCommentId=101174)
```c ++
class A {
public:
	A() {
		printf("A ");
	}
	~A() {
		printf("deA ");
	}
};

class B {
public:
	B() {
		printf("B ");
	}
	~B() {
		printf("deB ");
	}
};

class C : public A, public B {
public:
	C() {
		printf("C ");
	}
	~C() {
		printf("deC ");
	}
};

int main()
{
	A *a = new C();
	delete a;

	return 0;
}
```

- [x] A. A B C deA
- [ ] B. C A B deA
- [ ] C. A B C deC
- [ ] D. C A B deC
