### 1. 标题：[星际密码](https://www.nowcoder.com/questionTerminal/34f17d5f2a8240bea661a23ec095a062)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题实质上是一个菲波那切数列的变相问题。如下图所示：<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/day25Solution1.png)<br>

&#160; &#160; &#160; &#160; 因此，我们可以先初始化一个菲波那切数列 `array` ，接着根据输入的 `x` 值，按照格式输出所对应的 `array[x]` 即可。<br>

- **【代码】**
``` c ++
#include <iostream>
#include <vector>

using namespace std;

int main()
{
	//初始化菲波那切数列
	vector<int> array = { 1,1 };
	for (int i = 2; i < 10001; ++i) {
		array.push_back((array[i - 1] + array[i - 2]) % 10000);
	}

	//按照格式输入输出
	int n = 0, x = 0;
	while (cin >> n) {
		while (n--) {
			cin >> x;
			printf("%04d", array[x]);
		}
		printf("\n");
	}

	return 0;
}
```

### 2. 标题：[数根](https://www.nowcoder.com/questionTerminal/e2422543519249f292d8435394ab82fe)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 

- **【代码】**
``` c ++

```
