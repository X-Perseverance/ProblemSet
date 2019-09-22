### 1. 标题：[字符串反转](https://www.nowcoder.com/practice/e45e078701ab4e4cb49393ae30f1bb04?tpId=37&&tqId=21235&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 在反转字符串时，我们可以设置两个分别指向首尾位置的变量 left 和 right ，通过 `swap(str[left],str[right])` 交换首尾位置的字符，交换完后，`++left`，`--right`，直到 left 和 right 相遇就结束反转。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>

using namespace std;

string ReverseString(string str)
{
	if (str.empty())
		return str;

	size_t left = 0;
	size_t right = str.size() - 1;

	while (left < right) {
		swap(str[left], str[right]);
		++left;
		--right;
	}

	return str;
}

int main()
{
	string str;
	getline(cin, str);
	cout << ReverseString(str) << endl;

	return 0;
}
```

### 2. 标题：[公共字串计算](https://www.nowcoder.com/practice/98dc82c094e043ccb7e0570e5342dd1b?tpId=37&&tqId=21298&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以采用**动态规划**的思想来解题。<br>
&#160; &#160; &#160; &#160; 我们定义一个二维数组 `array` ，其中纵轴和横轴各自代表一个字符串，分别记为 str1 和 str2 ，而每一个 `array[i][j]` 代表的是 str1 以 str1[i-1] 结尾的字符串和 str2 以 str2[j-1] 结尾的字符串这两个字符串的最长公共子串的长度，初始值都置为0。在遍历两个字符串的时候（i 和 j 从1开始），若当前遍历的两个字符相同，也就是 `str1[i - 1] == str2[j - 1]` ，那么就有：`array[i][j] = array[i - 1][j - 1] + 1` ，根据这条规则我们就可以递推求出最长公共子串的长度。<br>

&#160; &#160; &#160; &#160; 举个例子，若 str1 为 `"abc"` ，str2 为 `"ababc"` ，那么就会有如下图所示的结果：<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/day19Array.png)<br>

&#160; &#160; &#160; &#160; 通过上图，我们发现这两个字符串的最长公共子串的长度为3。<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

void Lowercase(string& str) //转换为小写字符串
{ 
	for (size_t i = 0; i < str.size(); ++i) {
		if (str[i] >= 'A' && str[i] <= 'Z')
			str[i] += 32;
	}
}

int main()
{
	string str1, str2;

	while (cin >> str1 >> str2) {
		Lowercase(str1);
		Lowercase(str2);

		int size1 = str1.size();
		int size2 = str2.size();

		vector<vector<int>> array(size1 + 1, vector<int>(size2 + 1, 0));

		int maxLength = 0;

		for (int i = 1; i <= size1; ++i) {
			for (int j = 1; j <= size2; ++j) {
				if (str1[i - 1] == str2[j - 1])
					array[i][j] = array[i - 1][j - 1] + 1;
				if (array[i][j] > maxLength) {
					maxLength = array[i][j]; //记录当前公共子串的最大长度
				}
			}
		}

		cout << maxLength << endl;
	}

	return 0;
}
```
