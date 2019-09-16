### 1. 标题：[杨辉三角的变形](https://www.nowcoder.com/practice/8ef655edf42d4e08b44be4d777edbf43?tpId=37&&tqId=21276&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路一】**<br>

&#160; &#160; &#160; &#160; 常规方法，先构建 n 行杨辉三角数字数组，接着在最后一行中找第一个偶数即可。<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>

using namespace std;

int main() {
	int n = 0;

	while (cin >> n) {
		int i = 0, j = 0;
		vector<vector<int>> nums(n, vector<int>(2 * n - 1, 0));
		
		//第一步：构建n行杨辉三角数字数组
		nums[0][0] = 1;
		for (i = 1; i < n; ++i) {
			nums[i][0] = 1; //每一行的第一列都为1
			nums[i][2 * i] = 1; //每一行的最后一列都为1

			for (j = 1; j < 2 * i; ++j) {
				if (j == 1) //每一行的第二列只是上一行两个元素之和
					nums[i][j] = nums[i - 1][j - 1] + nums[i - 1][j];
				else //每一行的其他列是上一行三个元素之和
					nums[i][j] = nums[i-1][j-2] + nums[i - 1][j - 1] + nums[i - 1][j];
			}
		}
		
		//第二步：在最后一行中找第一个偶数
		for (i = 0; i < 2 * n - 1; ++i) {
			if (nums[n - 1][i] != 0 && nums[n - 1][i] % 2 == 0) {
				cout << i + 1 << endl;
				break;
			}
		}
		if (i == 2 * n - 1)
			cout << -1 << endl;
	}

	return 0;
}
```

- **【解题思路二】**<br>

&#160; &#160; &#160; &#160; 高级方法，通过找规律可快速解题。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int main() {
	int n = 0;

	while (cin >> n) {
		if (n <= 2)
			cout << -1 << endl;
		else if (n % 2 == 1)
			cout << 2 << endl;
		else if (n % 4 == 0)
			cout << 3 << endl;
		else
			cout << 4 << endl;
	}

	return 0;
}
```

### 2. 标题：[超长正整数相加](https://www.nowcoder.com/practice/5821836e0ec140c1aa29510fd05f45fc?tpId=37&&tqId=21301&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 对于这道题，我们可以从低位向高位依次相加，具体步骤如下：<br>
&#160; &#160; &#160; &#160; （1）计算对应位上的和：**对应位的值相加+上一位的进位值**；<br>
&#160; &#160; &#160; &#160; （2）将第一步计算出来的和对十取模，再将其转换为字符存入到结果中；<br>
&#160; &#160; &#160; &#160; （3）将第一步计算出来的和整除以十，作为当前位的进位值；<br>
&#160; &#160; &#160; &#160; （4）接着重复以上步骤计算下一位，直到每一位都相加完；<br>
&#160; &#160; &#160; &#160; （5）若相加完后，最后一次还有进位值产生，那么给结果再加一位1。最后，将结果进行整体逆置，得到最终结果。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

string AddLongInteger(string addend, string augend) {
	string ret; //保存相加结果
	int carry = 0; //进位值，初始值为0
	int len1 = addend.size() - 1;
	int len2 = augend.size() - 1;

	while (len1 >= 0 || len2 >= 0) { //从低位向高位依次相加
		if (len1 >= 0)
			carry += addend[len1] - '0';
		if (len2 >= 0)
			carry += augend[len2] - '0';
		
		ret += (char)(carry % 10 + '0'); //将当前位相加的值对十取模，再将其存入到ret中
		carry /= 10; //取进位值
		
		--len1;
		--len2;
	}

	if (carry == 1) //若相加完后还有进位，则进一位
		ret += '1';

	reverse(ret.begin(), ret.end()); //整体逆置

	return ret;
}

int main() {
	string str1, str2;

	while (cin >> str1 >> str2)
		cout << AddLongInteger(str1, str2) << endl;

	return 0;
}
```
