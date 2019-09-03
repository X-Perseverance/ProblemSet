### 1. 标题：[参数解析](https://www.nowcoder.com/practice/668603dc307e4ef4bb07bcd0615ea677?tpId=37&&tqId=21297&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题的要求是统计出给定字符串中的参数个数并输出每一个参数，题目中已经说明这些参数是通过空格来分隔的，但需要特别注意的是在双引号内的空格是作为正常字符要被输出的，并不作为分隔符，所以本题的关键就是要区分出引号内的空格和引号外的空格。为了加以区分，我们可以设置一个flag，若 flag 为 true，则表明当前是在一对引号内进行解析；若为 false，则表明不在一对引号内，这样就保证了引号内的空格能被正常输出。具体代码如下：<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>
#include <vector>

using namespace std;

int main() {
	string str;

	while (getline(cin, str)) {
		vector<string> ret; //保存每一个解析出来的参数
		string temp; //保存当前正在解析的参数
		bool flag = false; //引号标志，flag为true，表示在引号内，否则不在

		for (size_t i = 0; i < str.size(); ++i) {
			if (!flag) { //如果当前不在引号内
				if (str[i] == ' ') { //若遇到空格，则表明已解析完一个参数
					ret.push_back(temp);
					temp = "";
				}
				else if (str[i] == '"') //若遇到引号，则表明后续解析在一对引号内
					flag = true;
				else
					temp += str[i];
			}
			else { //如果当前在引号内
				if (str[i] == '"') //若遇到引号，则表明当前这对引号内的参数已遍历完
					flag = false;
				else
					temp += str[i];
			}
		}
        
		ret.push_back(temp); //将最后一个解析出来的参数添加到ret中

		cout << ret.size() << endl; //输出参数个数
		for (auto s : ret) //依次输出每一个参数
			cout << s << endl;
	}

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 在上述代码中，要格外注意最后一次 `ret.push_back(temp);`。因为字符串中的最后一个参数后面并没有空格来进行分隔，而是一个 `'\0'`，所以在 for 循环内，并没有将最后一个参数保存到 ret 中去，因此我们需要在 for 循环外再进行一次 push_back 操作。<br>

### 2. 标题：[跳石板](https://www.nowcoder.com/practice/4284c8f466814870bae7799a07d49ec8?tpId=85&&tqId=29852&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

> （1）创建一个数组 minSteps，长度为 m+1，保存从起始点到达每一个位置的最少跳跃次数，对该题而言起始点就是 n 位置；<br>
> （2）从起始点开始对 minSteps 进行遍历，计算出每一个位置上的约数，也就是求出从当前位置能到达哪些位置，接着更新那几个能到达的位置的最少跳跃次数；<br>
> （3）将 minSteps[m] 作为最终的结果输出即可。<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>
#include <climits>
#include <algorithm>

using namespace std;

int main() {
	int n = 0, m = 0;

	while (cin >> n >> m) {
		vector<int> minSteps(m + 1, INT_MAX); //minSteps 保存从起始点到达每一个位置的最少跳跃次数，并都初始化为最大值INT_MAX
		minSteps[n] = 0; //将起始点设为n

		for (size_t i = n; i <= m; ++i) { //计算从起始点到达每一个位置的最少跳跃次数
			if (minSteps[i] == INT_MAX) //如果到达当前位置的跳跃次数还是INT_MAX，则表明不能到达该位置，那么就更不可能从该位置到达别的位置，所以跳过当前位置
				continue;

			for (size_t j = 2; j <= sqrt(i); ++j) { //计算出当前位置的约数，以便于统计出从当前位置能到达哪些位置
				if (i%j == 0) {
					if (i + j <= m) //如果j是i的约数，那么说明从当前位置i可以跳跃j步到达i+j这个位置，所以在这里需要更新i+j这个位置的跳跃次数
						minSteps[i + j] = min(minSteps[i + j], minSteps[i] + 1);
					if (j != i / j && i + i / j <= m) //如果j是i的约数，那么i/j也是i的约数，从而从当前位置i可以跳跃i/j步到达i+i/j这个位置，所以在这里需要更新i+i/j这个位置的跳跃次数
						minSteps[i + i / j] = min(minSteps[i + i / j], minSteps[i] + 1);
				}
			}
		}

		if (minSteps[m] == INT_MAX) //如果到达m位置的跳跃次数还是INT_MAX，则表明不能到达该位置，输出-1
			minSteps[m] = -1;

		cout << minSteps[m] << endl;
	}

	return 0;
}
```
