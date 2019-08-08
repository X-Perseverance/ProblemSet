### 1. 标题：[统计回文](https://www.nowcoder.com/practice/9d1559511b3849deaa71b576fa7009dc?tpId=85&&tqId=29842&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题直接暴力求解，遍历字符串1，将字符串2插入到字符串1的每一个位置，然后判断插入后的字符串1是否是回文，若是就统计起来。<br>

- **【代码】**
```c++
#include <iostream>
#include <string>

using namespace std;

bool IsPalindrome(const string& str) { //判断一个字符串是否是回文
	size_t begin = 0;
	size_t end = str.size() - 1;
	while (begin < end)
	{
		if (str[begin] != str[end])
			return false;
		++begin;
		--end;
	}
	return true;
}

int main()
{
	std::string str1, str2;
	getline(cin, str1);
	getline(cin, str2);

	size_t count = 0;
	for (size_t i = 0; i <= str1.size(); ++i) //将字符串2插入到字符串1的每个位置，再判断是否是回文
	{
		string str = str1; //备份
		str.insert(i, str2);
		if (IsPalindrome(str))
			++count;
	}
	cout << count << endl;

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 在上述代码中，我们要特别注意两个地方：<br>
&#160; &#160; &#160; &#160; （1）在遍历字符串1时，一定要遍历到最后一个字符的下一个位置，即`i <= str1.size()`，因为这个位置也是插入情况之一，否则程序结果将出错。<br>
&#160; &#160; &#160; &#160; （2）在将字符串2插入字符串1时，我们不能直接改变原字符串1，否则后续的判断直接出错，而是每次都做一次备份，对这个备份字符串进行插入操作。<br>

### 2. 标题：[连续最大和](https://www.nowcoder.com/practice/5a304c109a544aef9b583dce23f5f5db?tpId=85&&tqId=29858&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 依次遍历数组array，若当前和大于0，则在原有基础上继续累加，因为还有可能更大；若小于0，则抛弃并将当前和重置为此时的遍历值array[i]，因为任何数加上一个负数反而更小了。与此同时，在遍历每一个元素时，都要保存当前可能遇到的最大和。<br>

- **【示例】**<br>

&#160; &#160; &#160; &#160; 数据：`1 -2 6 -3 5`<br>
&#160; &#160; &#160; &#160; 先将当前和curSum和最大和maxSum都置为数组第一个元素1，接着从下标1开始遍历数组。第一次，加上-2，当前和就变成了-1；第二次，加上6，在这里我们注意到由于此前的累计和是-1，那么用-1加上6得到的和是5，比6本身还小，也就是说从第一个数字开始的子数组的和会小于从第三个数字开始的子数组的和，因此我们不用考虑从第一个数字开始的子数组，之前的累加和也被抛弃，而是从第三个数字重新开始累加，此时得到的和是6；第三次，加上-3，和为3，我们又注意到，由于-3是一个负数，因此累加-3后得到的和比原来的和还要小，因此我们把之前得到的和6保存下来，它有可能是最大的子数组和；第四次，加上5，和为8，此时和比之前的和6还要大，所以把最大的子数组和由6更新为8。遍历完后，此时最大的子数组和为8，对应的子数组为`6 -3 5`。整个过程演示如下：<br>

| 步骤 | 操作 | 累加的子数组和 | 最大的子数组和 |
| :--: | :--: | :--: | :--: |
| 1 | 初始值 | 1 | 1 |
| 2 | 加-2 | -1 | 1 |
| 3 | 抛弃之前的和-1，加6 | 6 | 6 |
| 4 | 加-3 | 3 | 6 |
| 5 | 加5 | 8 | 8 |

- **【代码】**
```c++
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
	int n;
	cin >> n;
	vector<int> array;
	array.resize(n);
	for (int i = 0; i < n; ++i)
		cin >> array[i];

	int curSum = array[0], maxSum = array[0];
	for (int i = 1; i < n; ++i)
	{
		if (curSum < 0) //抛弃当前和并将其重置为此时的遍历值array[i]
			curSum = array[i];
		else //在原有基础上继续累加
			curSum += array[i];
		
		maxSum = max(maxSum, curSum); //保存可能遇到的最大子数组和
	}
	cout << maxSum << endl;

	return 0;
}
```
