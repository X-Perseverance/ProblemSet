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

&#160; &#160; &#160; &#160; 本题可以采用**动态规划**的思想来进行解题，具体思路如下：<br>
&#160; &#160; &#160; &#160; 我们先定义一个二维布尔型数组 array[wildcardLength+1][matchedLength+1] ，其中纵轴代表带有通配符的字符串 wildcardString ， 横轴代表要匹配的字符串 matchedString ，而数组中的每一个值 array[i][j] 代表的是 wildcardString 的前 i 个字符与 matchedString 的前 j 个字符是否匹配，若匹配则为 true ，否则为 false 。<br>

&#160; &#160; &#160; &#160; 举个例子，比如 wildcardString 为 "?b*e" ，matchedString 为 "abcde" ，那么我们就可以定义出如下图所示的二维数组：<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/day18Array1.png)<br>

&#160; &#160; &#160; &#160; 通过观察上图，我们发现在定义二维数组时多加了一行和一列，并将这一行和一列作为整个数组的初始值，也许在这里你会有一些疑惑，但这样设置的原因我们在后面再进行解释。<br>

&#160; &#160; &#160; &#160; 接着我们再来讨论如何根据这些初始值来填满这个二维数组，此时可分为以下四种情况：（i 和 j 从1开始）<br>
&#160; &#160; &#160; &#160; （1）`wildcardString[i-1] != matchedString[j-1]` ，对于这种情况有：`array[i][j] = false`；<br>
&#160; &#160; &#160; &#160; （2）`wildcardString[i-1] == matchedString[j-1]` ，对于这种情况有：`array[i][j] = array[i-1][j-1]`；<br>
&#160; &#160; &#160; &#160; （3）`wildcardString[i-1] == '?'` ，对于这种情况，由于 ? 可以匹配任意1个字符，所以有：`array[i][j] = array[i-1][j-1]`；<br>
&#160; &#160; &#160; &#160; （4）`wildcardString[i-1] == '*'` ，对于这种情况，由于 * 可以匹配0个或以上的字符，所以还需分情况讨论：<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; a. 当 * 匹配 0 个字符时，有：array[i][j] = array[i][j-1];<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; b. 当 * 匹配 1 个字符时，有：array[i][j] = array[i-1][j-1];<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; c. 当 * 匹配 2 个字符时，有：array[i][j] = array[i-2][j-1];<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; d. 当 * 匹配 3 个字符时，有：array[i][j] = array[i-3][j-1];<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; ......<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; 综上所述，整理后的结果就是：`array[i][j] = array[i][j-1] || array[i-1][j-1] || array[i-2][j-1] || array[i-3][j-1] || ... || array[0][j-1]`。<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; 而按照上述公式，又可以得到：`array[i-1][j] = array[i-1][j-1] || array[i-2][j-1] || array[i-3][j-1] || ... || array[0][j-1]`。<br>
&#160; &#160; &#160; &#160; &#160; &#160; &#160; &#160; 所以，在这种情况下有：`array[i][j] = array[i][j-1] || array[i-1][j]`。<br>

&#160; &#160; &#160; &#160; 还是之前的例子，那么通过上面的讨论，我们就可以得到如下图所示的结果：<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/day18Array2.png)<br>

&#160; &#160; &#160; &#160; 当整个数组都填完后，array[wildcardLength][matchedLength] 就是最终的匹配结果。<br>
&#160; &#160; &#160; &#160; 最后，我们再来说一说在定义二维数组时为什么要多加一行和一列。在上面的讨论中，我们发现若当前遍历的字符是匹配的，那么截止到当前字符的字符串是否匹配就由该字符之前的字符串决定了，也就是说后续的判断结果会依据之前的判断结果，所以在开始匹配第一个字符时，我们可能就要依据初始值来决定判断结果。在设置了初始值后，通过递推我们就可以依次填满整个数组。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>
#include <vector>

using namespace std;

bool Match(string wildcardString, string matchedString) {
	int size1 = wildcardString.size();
	int size2 = matchedString.size();

	vector<vector<bool>> array(size1 + 1, vector<bool>(size2 + 1, false));
	array[0][0] = true; //（1）

	for (int i = 1; i <= size1; ++i) {
		char ch1 = wildcardString[i - 1];

		array[i][0] = array[i - 1][0] && (ch1 == '*'); //（2）

		for (int j = 1; j <= size2; ++j) {
			char ch2 = matchedString[j - 1];

			if (ch1 == '*') //第四种情况
				array[i][j] = array[i - 1][j] || array[i][j - 1];
			else //前三种情况合为一种
				array[i][j] = array[i - 1][j - 1] && ((ch1 == ch2) || (ch1 == '?'));
		}
	}

	return array[size1][size2];
}

int main() {
	string wildcardString, matchedString;

	while (cin >> wildcardString >> matchedString) {
		if (Match(wildcardString, matchedString))
			cout << "true" << endl;
		else
			cout << "false" << endl;
	}

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; （1）在上述代码中我们将 array[0][0] 设置为 true，这是因为最开始的两个空串是匹配的；<br>
&#160; &#160; &#160; &#160; （2）在代码中还有这样一条语句：`array[i][0] = array[i - 1][0] && (ch1 == '*');` ，这是为了应对类似于 `"*a"` 和 `"a"` 这样的情况。由于 `*` 和 `""` 是匹配的，所以若当前为 *，并且之前的字符串也匹配，那么在设置初始值时就应该置为true。<br>
