### 1. 标题：[另类加法](https://www.nowcoder.com/practice/e7e0d226f1e84ba7ab8b28efc6e1aebc?tpId=8&&tqId=11065&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 由于题目要求不得使用+或其他算数运算符，所以本题可以从位运算入手。我们发现，当两个数做二进制加法时，如果不考虑进位，那么两个数进行异或运算即可求出每一个位上的和，如：0101+1001->1100。接着再来考虑进位，只有当两个二进制数中的某一个位都为1时，才会产生进位，出现进位会使当前位置为0，高一位加一，而在前面我们进行异或运算时，已经让产生进位的位置为0，所以题目所求和就是两个数进行异或运算的结果加上进位值（进位值可以通过两个数相与再左移一位来计算），此时又要计算异或值和进位值的和，那么我们可以不断循环求和，直到没有进位产生为止。<br>

- **【代码】**
```c
int addAB(int A, int B) {
	int sum = A, carry = 0;
	while (B != 0) {
		sum = A ^ B; //不考虑进位时的和
		carry = (A&B) << 1; //进位值
		A = sum;
		B = carry;
	}
	return sum;
}
```

### 2. 标题：[求路径总数](https://www.nowcoder.com/practice/e2a22f0305eb4f2f9846e7d644dba09b?tpId=37&&tqId=21314&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/NumberOfPaths.png)<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int Path(int n, int m) {
	if ((n == 1 && m >= 1) || (m == 1 && n >= 1)) //只有一行或一列
		return m + n;
	else if (n > 1 && m > 1) //多行多列
		return Path(n - 1, m) + Path(n, m - 1);
	else //无格子
		return 0;
}

int main()
{
	int n = 0, m = 0;

	while (cin >> n >> m) {
		cout << Path(n, m) << endl;
	}

	return 0;
}
```
