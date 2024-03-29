### 1. 以下for循环的执行次数是（）
```c
for(x=0,y=0; (y=123)&&(x<4); x++);
```
- [ ] A. 是无限循环
- [ ] B. 循环次数不定
- [x] C. 4次
- [ ] D. 3次

> **【分析】**<br>
> &#160; &#160; &#160; &#160; `y=123` 这条赋值语句结果是非零值，即为逻辑真，所以循环次数只与 `x` 有关。

### 2. 以下程序的运行结果是（）
```c
int main(void)
{
        printf("%s , %5.3s\n", "computer", "computer");
        return 0;
}
```
- [ ] A. computer , puter
- [x] B. computer ,   com
- [ ] C. computer , computer
- [ ] D. computer , compu.ter

> **【分析】**<br>
> &#160; &#160; &#160; &#160; 对于 `%m.ns` 这种格式的输出，可分两种情况讨论：<br>
> &#160; &#160; &#160; &#160; 若 `m>=n` ，则输出总长度为 m ，但只取字符串中左端 n 个字符，并输出在 m 列的右侧，而左侧全补空格；<br>
> &#160; &#160; &#160; &#160; 若 `m<n` ，则输出字符串左端 n 个字符。

### 3. `int *p[4]` 与选项中的（）等价
- [ ] A. int p[4]
- [ ] B. int *p
- [x] C. int *(p[4])
- [ ] D. int (*p)[4]

> **【分析】**<br>
> &#160; &#160; &#160; &#160; 由于 `[]` 的优先级高于 `*`，所以题中 p 是一个指针数组，共有4个元素，每个元素都是一个指针。

### 4. 若有定义语句：`int year=1009, *p=&year;` 以下不能使变量 year 中的值增至 1010 的语句是（）
- [ ] A. *p+=1
- [ ] B. (*p)++
- [ ] C. ++(*p)
- [x] D. *p++

> **【分析】**<br>
> &#160; &#160; &#160; &#160; D选项中 `++` 的优先级高于 `*`，即对 p 先进行自增运算，让 p 指向 year 后面的地址空间，然后进行取值操作，整个过程并不会改变 year 的值。

### 5. 若有定义语句：`int a=10; double b=3.14;` 则表达式 'A'+a+b 值的类型是（）
- [ ] A. char
- [ ] B. int
- [x] C. double
- [ ] D. float

### 6. 在（）情况下适宜采用 inline 定义内联函数
- [ ] A. 函数体含有循环语句
- [ ] B. 函数体含有递归语句
- [x] C. 函数代码少、频繁调用
- [ ] D. 函数代码多，不常调用

### 7. 在 c++ 语言中，对函数参数默认值描述正确的是（）
- [ ] A. 函数参数的默认值只能设定一个
- [ ] B. 一个函数的参数若有多个，则参数默认值的设定可以不连续
- [ ] C. 函数参数必须设定默认值
- [x] D. 在设定了参数的默认值后，该参数后面定义的所有参数都必须设定默认值

### 8. 下列静态数据成员的特性中，错误的是（）
- [ ] A. 引用静态数据成员时，要在静态数据成员名前加<类名>和作用域符号
- [ ] B. 说明静态数据成员时前边要加关键字static来修饰
- [ ] C. 静态数据成员在类体外进行初始化
- [x] D. 静态数据成员不是所有对象所共有的

### 9. 表达式 11|10 的结果是（）（本题数值均为十进制）
- [x] A. 11
- [ ] B. 10
- [ ] C. 8
- [ ] D. 2

> **【技巧】**<br>
> &#160; &#160; &#160; &#160; 对两个进行按位或的正数来说，它们的结果一定大于等于它们中的任意一个。

### 10. 下面叙述不正确的是（）
- [ ] A. 派生类一般都用公有派生
- [ ] B. 对基类成员的访问必须是无二义性的
- [ ] C. 赋值兼容规则也适用于多重继承的组合
- [x] D. 父类的公有成员在派生类中仍然是公有的
