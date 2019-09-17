### 1. 标题：[统计每个月兔子的总数](https://www.nowcoder.com/practice/1221ec77125d4370833fd3ad5ba72395?tpId=37&&tqId=21260&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题实质上是一个**斐波那锲数列**的变相应用。我们从题目可以知道：第一个月和第二个月的兔子数量都为1，但**从第三个月开始，每月的兔子数 f(n) 都由两部分组成，一部分是原来的兔子数，也就是上个月的兔子数 f(n-1)；另一部分是新生的小兔子数，也就是上上个月满足生育要求的兔子数 f(n-2)**，用公式表示就是：`f(n)=f(n-1)+f(n-2)`。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int getTotalCount(int monthCount)
{
	int first = 1;
	int second = 1;
	int result = 1;

	for (int i = 3; i <= monthCount; ++i) {
		result = first + second;
		first = second;
		second = result;
	}

	return result;
}

int main() {
	int month = 0;

	while (cin >> month)
		cout << getTotalCount(month) << endl;

	return 0;
}
```

### 2. 标题：[字符串通配符](https://www.nowcoder.com/practice/43072d50a6eb44d2a6c816a283b02036?tpId=37&&tqId=21294&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 

- **【代码】**
```c ++

```
