### 1. 标题：[计算糖果](https://www.nowcoder.com/practice/02d8d42b197646a5bbd0a98785bb3a34?tpId=85&&tqId=29857&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 这道题其实实质上就是一道三元一次方程求解的问题，所以做起来还是相对容易点。不过在编程的过程中，我们需要考虑到实际情况，因为在现实生活中，每个人手上的糖果数不可能为小数，也更不可能是负数，所以在求解时要注意过滤掉这些不切实际的结果。<br>

- **【代码】**<br>
```c++
#include <iostream>

using namespace std;

int main() {
	int arr[4] = { 0 };

	while (cin >> arr[0] >> arr[1] >> arr[2] >> arr[3]) {
		int a = 0, b = 0, c = 0;
		if ((arr[0] + arr[2]) % 2 == 0) { //需考虑a，b，c都为整数
			a = (arr[0] + arr[2]) >> 1;
			b = arr[2] - a;
			c = arr[3] - b;
			if (b - c == arr[1] && a >= 0 && b >= 0 && c >= 0) //需考虑a，b，c都为非负数
				cout << a << " " << b << " " << c << endl;
			else
				cout << "No" << endl;
		}
		else
			cout << "No" << endl;
	}

	return 0;
}
```

### 2. 标题：[进制转换](https://www.nowcoder.com/practice/ac61207721a34b74b06597fe6eb67c52?tpId=85&&tqId=29862&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 对该题而言，对一个十进制数进行进制转换无非就是想求出转换后的数每一个进制位上的值。我们都知道，任何一个十进制数M转换成N进制数后，它们之间有这样一个数学关系：`M = X₀*N⁰ + X₁*N¹ + X₂*N² + ...`，而这些系数（X₀、X₁、X₂）就是我们所要得到的，所以我们可以让这个十进制数对N进行取模得到余数即为当前低位X₀的值，然后再将其和进制数N相除，从而进入下一个进制位X₁的计算，以此类推，直到得到所有进制位上的值。运算推演如下图所示：<br>

| 操作 | M值 | M%N |
| :--: | :--: | :--: |
| 无 | `M = X₀*N⁰ + X₁*N¹ + X₂*N² + ...` | X₀ |
| M/N | `M = X₁*N⁰ + X₂*N¹ + X₃*N² + ...` | X₁ |
| M/N | `M = X₂*N⁰ + X₃*N¹ + X₄*N² + ...` | X₂ |
| ... | ... | ... |

- **【代码】**<br>
```c++
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

int main() {
	int m = 0, n = 0;

	while (cin >> m >> n) {
		string ret, hashTable = "0123456789ABCDEF";

		int flag = false;
		if (m < 0) { //判断m是否为负数，若是则将其转换为正数，并进行标记
			flag = true;
			m = -m;
		}

		while (m) { //按进制换算成对应的字符添加到字符串ret
			ret += hashTable[m%n];
			m /= n;
		}

		if (flag) //若是负数，则还原负号
			ret += '-';

		reverse(ret.begin(), ret.end()); //将字符串ret进行逆置，以作为最终结果
		cout << ret << endl;
	}

	return 0;
}
```
