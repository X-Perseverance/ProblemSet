### 1. 标题：[杨辉三角的变形](https://www.nowcoder.com/practice/8ef655edf42d4e08b44be4d777edbf43?tpId=37&&tqId=21276&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路一】**<br>

&#160; &#160; &#160; &#160; 常规方法，先构建 n 行的杨辉三角数字数组，接着在最后一行中找第一个偶数即可。<br>

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

&#160; &#160; &#160; &#160; 

- **【代码】**
```c ++

```
