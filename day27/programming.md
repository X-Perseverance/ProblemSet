### 1. 标题：[不用加减乘除做加法](https://www.nowcoder.com/questionTerminal/59ac416b4b944300b617d4f7f111b215)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 对本题来说，我们可以将十进制数的加法运算转换为二进制数的位运算，从而避免了使用加减乘除，具体步骤如下：<br>

> （1）先不考虑进位求两数之和，也就是：`sum = num1 ^ num2`；<br>
> （2）再求出两数相加时产生的进位值，也就是：`carry = (num1 & num2) << 1`；<br>
> （3）最后计算出 sum 和 carry 的和即可，此时可以把 sum 看做 num1 ，把 carry 看做 num2 ，从第一步开始循环计算，直到进位值为0时就停止循环，此时 sum 就是最终的结果。<br>

- **【代码】**
``` c ++
class Solution {
public:
	int Add(int num1, int num2)
	{
		while (num2 != 0) { //当不产生进位时，停止循环
			int sum = num1 ^ num2; //不考虑进位时两数之和
			int carry = (num1 & num2) << 1; //进位值
			num1 = sum;
			num2 = carry;
		}

		return num1;
	}
};
```

### 2. 标题：[三角形](https://www.nowcoder.com/questionTerminal/c67a09062c0f4a5b964eef0945d3dd06)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 由于一个合法的三角形的**任意两边之和都是大于第三边的**，所以我们可以对输入的三个数字分别进行两两相加再与另一个数进行比较，若比较结果都是大于，那么这三个数就可以组成三角形；否则不能。<br>

- **【代码一】**
``` c ++
#include <iostream>

using namespace std;

int main()
{
	double a = 0, b = 0, c = 0;

	while (cin >> a >> b >> c)
	{
		if ((a + b > c) && (a + c > b) && (b + c > a))
			cout << "Yes" << endl;
		else
			cout << "No" << endl;
	}

	return 0;
}
```

- **【代码二】**
``` c ++
#include <iostream>
#include <string>

using namespace std;

bool Great(string str1, string str2) //比较两个数字字符串的大小
{
	size_t size1 = str1.size();
	size_t size2 = str2.size();

	if (size1 > size2)
		return true;
	else if (size1 < size2)
		return false;
	else
		return str1 > str2;
}

string Add(string str1, string str2) //计算两个数字字符串的和
{
	string ret; //保存相加结果
	int carry = 0; //进位值
	int len1 = str1.size() - 1;
	int len2 = str2.size() - 1;

	while (len1 >= 0 || len2 >= 0) { //从低位向高位依次相加
		if (len1 >= 0)
			carry += str1[len1] - '0';
		if (len2 >= 0)
			carry += str2[len2] - '0';

		ret = (char)(carry % 10 + '0') + ret; //将当前位相加的值对十取模，再将其存入到ret中
		carry /= 10; //取进位值

		--len1;
		--len2;
	}

	if (carry == 1) //若相加完后还有进位，则进一位
		ret = '1' + ret;

	return ret;
}

int main()
{
	string a, b, c;

	while (cin >> a >> b >> c) {
		if (Great(Add(a, b), c) && Great(Add(a, c), b) && Great(Add(b, c), a))
			cout << "Yes" << endl;
		else
			cout << "No" << endl;
	}

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 在本题中，我们需要特别注意输入数据 a b c 的取值范围，即 `1≤a, b, c≤10^100` 。在第一份代码中，我们使用 **double** 来定义变量，因为 double 类型数据的取值范围为 `1.7E-308 ~ 1.7E+308` ，所以可以满足题目要求。在第二份代码中，我们使用 **string** 来定义变量，并额外定义了字符串比较以及字符串相加的函数，这样就将大数相加比较问题转变成了字符串相加比较问题。<br>
