### 1. 标题：[微信红包](https://www.nowcoder.com/practice/fbcf95ed620f42a88be24eb2cd57ec54?tpId=49&&tqId=29311&rp=1&ru=/activity/oj&qru=/ta/2016test/question-ranking)
- **【解题思路一】**<br>

&#160; &#160; &#160; &#160; 为了找出这个过半的数，我们可以用变量 count 记录每个数变化的次数，用变量 ret 记录可能过半的数，初始值都为 0 。首先让 count=0，ret=0，接着从头开始往后遍历数组，如果 count 为 0 ，就让 ret=gifts[i]，并置 count=1 ，否则的话再判断 gifts[i] 与 ret 是否相等，相等就给 count++ ，不相等就 count-- ，如此遍历一遍，那么 ret 就有可能是所要找的那个数。最后，再次遍历数组检查 ret 的出现次数是否超过数组长度的一半即可。<br>

- **【代码】**
```c ++
class Gift {
public:
	int getValue(vector<int> gifts, int n) {
		if (n <= 0)
			return 0;

		//找出可能满足题意的数
		int ret = 0, count = 0;
		for (int i = 0; i < n; ++i) {
			if (count == 0) {
				ret = gifts[i];
				count = 1;
			}
			else {
				if (gifts[i] == ret)
					++count;
				else
					--count;
			}
		}

		//检查上述结果的出现次数是否超过数组长度一半
		count = 0;
		for (int i = 0; i < n; ++i) {
			if (gifts[i] == ret)
				++count;
		}
		return (count > n / 2) ? ret : 0;
	}
};
```

- **【解题思路二】**<br>

&#160; &#160; &#160; &#160; **在数组中若有一个数的出现次数超过了一半，那么排序过后，这个数必然在数组中间**。所以对本题来说，我们只需要检查排序后位于数组中间的数的出现次数是否超过数组长度的一半即可。<br>

- **【代码】**
```c ++
class Gift {
public:
	int getValue(vector<int> gifts, int n) {
		if (n <= 0)
			return 0;

		sort(gifts.begin(), gifts.end()); //排升序

		int middle = gifts[n / 2]; //排序之后过半的数必然在数组中间

		int count = 0; //检查middle的出现次数是否超过数组长度一半
		for (int i = 0; i < n; i++) {
			if (gifts[i] == middle)
				count++;
		}
		return (count > n / 2) ? middle : 0;
	}
};
```

### 2. 标题：[计算字符串的距离](https://www.nowcoder.com/practice/3959837097c7413a961a135d7104c314?tpId=37&&tqId=21275&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以采用**动态规划**的思想来解题。<br>
&#160; &#160; &#160; &#160; 我们需要定义一个二维数组 array ，其中纵轴代表字符串 charA，横轴代表字符串 charB，而每一个 array[i][j] 代表的是 charA[0...i-1] 编辑成 charB[0...j-1] 的操作次数。由于许可的编辑操作包括将一个字符替换成另一个字符，插入一个字符以及删除一个字符，所以递推公式为：`array[i][j] = min{ array[i-1][j-1]+((charA[i-1]==charB[j-1])?0:1), array[i-1][j]+1, array[i][j-1]+1 }`，解释如下：<br>
&#160; &#160; &#160; &#160; （1）`array[i - 1][j - 1] + ((charA[i - 1] == charB[j - 1]) ? 0 : 1)`<br>
&#160; &#160; &#160; &#160; 这部分表示替换操作的操作次数，也就是将字符 charA[i-1] 替换成字符 charB[j - 1] 的操作次数与将 charA[0...i-2] 编辑成 charB[0...j-2] 的操作次数之和，如果当前字符 charA[i-1] 和 charB[j - 1] 相等，那就不需要替换，即替换字符的操作次数为0，否则就需要替换，操作次数为1。<br>
&#160; &#160; &#160; &#160; （2）`array[i - 1][j] + 1`<br>
&#160; &#160; &#160; &#160; 这部分表示删除操作的操作次数，也就是删除字符 charA[i-1] 的操作次数与将 charA[0...i-2] 编辑成 charB[0...j-1] 的操作次数之和，其中删除字符的操作次数为1。<br>
&#160; &#160; &#160; &#160; （3）`array[i][j - 1] + 1`<br>
&#160; &#160; &#160; &#160; 这部分表示插入操作的操作次数，也就是插入字符 charB[j-1] 的操作次数与将 charA[0...i-1] 编辑成 charB[0...j-2] 的操作次数之和，其中插入字符的操作次数为1。<br>
&#160; &#160; &#160; &#160; 以上就是分别采用不同的编辑操作将 charA[0...i-1] 编辑成 charB[0...j-1] 的操作次数，那么最少的操作次数就是这三者的最小值。<br>

- **【示例】**<br>

&#160; &#160; &#160; &#160; 假设 charA 为 `"aba"` ，charB 为 `"aac"` ，那么就会有如下图所示的结果：<br>

![image](https://github.com/X-Perseverance/ProblemSet/blob/master/images/day23Array.png)<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int  calStringDistance(string charA, string charB)
{
	int sizeA = charA.size();
	int sizeB = charB.size();

	if (sizeA == 0 || sizeB == 0)
		return max(sizeA, sizeB);

	vector<vector<int>> array(sizeA + 1, vector<int>(sizeB + 1, 0));

	for (int i = 1; i <= sizeA; ++i) //将 charA[0...i-1] 编辑成 "" 的操作次数
		array[i][0] = i;
	for (int j = 1; j <= sizeB; ++j) //将 "" 编辑成 charB[0...j-1] 的操作次数
		array[0][j] = j;

	for (int i = 1; i <= sizeA; ++i) {
		for (int j = 1; j <= sizeB; ++j) {
			array[i][j] = min(array[i - 1][j - 1] + ((charA[i - 1] == charB[j - 1]) ? 0 : 1), min(array[i - 1][j] + 1, array[i][j - 1] + 1));
		}
	}

	return array[sizeA][sizeB];
}

int main() 
{
	string str1, str2;

	while (cin >> str1 >> str2)
		cout << calStringDistance(str1, str2) << endl;

	return 0;
}
```
