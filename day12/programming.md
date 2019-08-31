### 1. 标题：[二进制插入](https://www.nowcoder.com/practice/30c1674ad5694b3f8f0bc2de6f005490?tpId=8&&tqId=11019&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题要求把 m 的二进制数位插入到 n 的二进制的第 j 位到第 i 位，那么我们只需要把 m 先左移 j 位，然后再将移位后的结果与 n 进行或运算即可。<br>

- **【代码】**
```c ++
class BinInsert {
public:
    int binInsert(int n, int m, int j, int i) {
        m <<= j;
        return n | m;
    }
};
```

### 2. 标题：[查找组成一个偶数最接近的两个素数](https://www.nowcoder.com/practice/f8538f9ae3f1484fb137789dec6eedb9?tpId=37&&tqId=21283&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题首先需要判断素数，素数表示除了1和本身不能被其它数所整除的数，我们可以通过循环遍历来判断一个数是否为素数。接着再来看如何找出最近的两个素数？最近的两个素数应该从中间的位置开始向两边查找，这样效率是最快的。<br>

- **【代码】**
```c ++
#include <iostream>
#include <algorithm>

using namespace std;

bool IsPrimeNumber(int num) { //判断素数
	int tmp = sqrt(num);
	for (int i = 2; i <= tmp; ++i) {
		if (num % i == 0)
			return false;
	}
	return true;
}

int main()
{
	int num;

	while (cin >> num) {
		int i = num / 2;
		for ( ; i > 0; --i) { //从中间向两边查找满足题意的素数	
			if (IsPrimeNumber(i) && IsPrimeNumber(num - i))
				break;
		}
		cout << i << endl << num - i << endl;
	}

	return 0;
}
```
