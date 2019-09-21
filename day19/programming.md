### 1. 标题：[汽水瓶](https://www.nowcoder.com/practice/fe298c55694f4ed39e256170ff2c205f?tpId=37&&tqId=21245&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路一】**<br>

&#160; &#160; &#160; &#160; 常规方法，在每一次兑换中，我们分别统计出当前用空瓶兑换的汽水数 exchangeBottle 和剩余的空瓶数 emptyBottle ，那么下一次兑换时总的空瓶数就变为 emptyBottle 和 exchangeBottle 之和，重复上述步骤并累加兑换的汽水数，直到空瓶数少于3个就兑换结束。要注意的是，若空瓶数剩余2个，那么还可以再换一瓶，结果还需加一。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int Exchange(int n)
{
	int result = 0;

	while (n > 1) {
		int exchangeBottle = n / 3; //用空瓶兑换的汽水
		result += exchangeBottle; //结果累加

		int emptyBottle = n % 3; //剩余的空瓶数
		n = emptyBottle + exchangeBottle; //下一次可兑换的空瓶数

		if (n == 2) { //若只剩余两个空瓶，则可以再换一瓶汽水
			++result;
			break;
		}
	}

	return result;
}

int main()
{
	int n = 0;

	while (cin >> n) {
		if (n == 0)
			break;
		cout << Exchange(n) << endl;
	}

	return 0;
}
```

- **【解题思路二】**<br>

&#160; &#160; &#160; &#160; 高级方法，由题可知，我们最少使用2个空瓶就可以换一瓶汽水，不过此时喝完后的空瓶需要还给老板，不能计入下次兑换的空瓶数，所以我们每一次只用2个空瓶去兑换汽水，这样用最少的成本才能得来最多的收益，也就是说我们只需要统计出总空瓶数中有多少个2就可以计算出结果。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int main()
{
	int n = 0;

	while (cin >> n) {
		if (n == 0)
			break;
		cout << n / 2 << endl;
	}

	return 0;
}
```

### 2. 标题：[查找两个字符串a,b中的最长公共子串](https://www.nowcoder.com/practice/181a1a71c7574266ad07f9739f791506?tpId=37&&tqId=21288&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以采用**动态规划**的思想来解题。<br>
&#160; &#160; &#160; &#160; 我们定义一个二维数组 `array` ，其中纵轴代表两个字符串中较短的那一个，记为 `str1` ，横轴代表较长的那一个，记为 `str2` ，而每一个 `array[i][j]` 代表的是短字符串 str1 的前 i 个字符和长字符串 str2 的前 j 个字符公共子串的长度，初始值都置为0。在遍历两个字符串的时候（i 和 j 从1开始），若当前遍历的两个字符相同，也就是 `str1[i - 1] == str2[j - 1]` ，那么就有：`array[i][j] = array[i - 1][j - 1] + 1` ，根据这条规则我们就可以递推求出最长的公共子串。<br>

&#160; &#160; &#160; &#160; 举个例子，若 str1 为 `"abc"` ，str2 为 `"ababc"` ，那么就会有如下图所示的结果：<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/day19Array.png)<br>

&#160; &#160; &#160; &#160; 通过上图，我们发现这两个字符串的最长公共子串就是 `"abc"` 。<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main() {
	string str1, str2;

	while (cin >> str1 >> str2) {
		int size1 = str1.size();
		int size2 = str2.size();

		if (size1 > size2) //让str1为较短字符串
			str1.swap(str2);

		vector<vector<int>> array(size1 + 1, vector<int>(size2 + 1, 0));

		int maxLength = 0, begin = 0;

		for (int i = 1; i <= size1; ++i) {
			for (int j = 1; j <= size2; ++j) {
				if (str1[i - 1] == str2[j - 1])
					array[i][j] = array[i - 1][j - 1] + 1;
				if (array[i][j] > maxLength) {
					maxLength = array[i][j]; //记录当前公共子串的最大长度
					begin = i - maxLength; //记录当前最长公共子串在短字符串str1中的起始位置
				}
			}
		}

		cout << str1.substr(begin, maxLength) << endl;
	}

	return 0;
}
```
