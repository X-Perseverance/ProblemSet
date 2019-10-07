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

&#160; &#160; &#160; &#160; 本题很容易理解，就是对输入数据的每一位进行累加求和，若得到的总和是一个一位数，则输出；若不是，则对该总和的每一位再累加求和，直到求出的总和是一个一位数。<br>

- **【代码】**
``` c ++
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string str;

	while (cin >> str) { //按照字符串格式输入，避免数字过大
		int sum = 0;
		for (size_t i = 0; i < str.size(); ++i) //将每一位进行相加得到总和
			sum += str[i] - '0';

		while (sum > 9) { //若总和不是一个一位数，那么对该总和的每一位再求和，直到求出的总和是一个一位数
			int temp = 0;
			while (sum > 0) { //将每一位进行相加得到总和
				temp += sum % 10;
				sum /= 10;
			}
			sum = temp;
		}

		cout << sum << endl;
	}

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 在上述代码中，我们注意到在输入数据时是按照字符串格式输入的，这是因为题目所给的数据范围为 `1 ≤ n ≤ 10E1000` ，这远远超过了 int 或 long 类型所能表示的数据范围，所以为了避免出现大数问题，我们才采用字符串这种输入格式。<br>
