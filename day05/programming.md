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

&#160; &#160; &#160; &#160; 

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
		if (curSum < 0)
			curSum = array[i];
		else
			curSum += array[i];
		
		maxSum = max(maxSum, curSum);
	}
	cout << maxSum << endl;

	return 0;
}
```
