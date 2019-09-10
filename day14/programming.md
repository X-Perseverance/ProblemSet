### 1. 标题：[计算日期到天数转换](https://www.nowcoder.com/practice/769d45d455fe40b385ba32f97e7bcded?tpId=37&&tqId=21296&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 创建一个二维数组，分别保存平年和闰年每月的天数，接着根据输入的年月日对三个变量进行判断（判断年是否为闰年，判断月是否合法，判断日是否合法），若都合法，那么累加求和即可求出所转换后的天数。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int main()
{
	int days[2][13] = {
		{0,31,28,31,30,31,30,31,31,30,31,30,31},
		{0,31,29,31,30,31,30,31,31,30,31,30,31} };
	
	int year = 0, month = 0, day = 0;

	while (cin >> year >> month >> day) {
		int flag = 0; //闰年标志
		int sum = 0;
		if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) //year是否为闰年
			flag = 1;
		if (month > 0 && month < 13) { //month是否合法
			if (day > 0 && day <= days[flag][month]) { //day是否合法
				while (--month) //累加天数
					sum += days[flag][month];
				sum += day;
				cout << sum << endl;
			}
			else
				cout << "-1" << endl;
		}
		else
			cout << "-1" << endl;
	}

	return 0;
}
```

### 2. 标题：[幸运的袋子](https://www.nowcoder.com/practice/a5190a7c3ec045ce9273beebdfe029ee?tpId=85&&tqId=29839&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 对于这道题，我们先给出一个结论：**对于任意两个正整数a和b，如果满足 a+b>ab，则必有一个数为1**。这句结论可用数论证明：设 a=1+m，b=1+n（a 和 b 都为正整数），若 1+m+1+n>(1+m)(1+n)，即 mn<1，那么 m 和 n 中必有一个0，所以 a 和 b 中必有一个1。现在我们把它推广到任意 K 个正整数上，假设有一个正整数集合 a1,a2,...,ak ，它们的和不大于积，但如果再来一个数能够使其满足和大于积，那么这个数必然为1，且为必要非充分条件；反之，若这个数大于1，那么更不可能满足和大于积的要求。<br>
&#160; &#160; &#160; &#160; 由此，我们可以按照如下的思路来解题：<br>
&#160; &#160; &#160; &#160; （1）将袋子中小球的号码进行升序排序；<br>
&#160; &#160; &#160; &#160; （2）判断这个袋子中是否有号码为1的小球。如果没有，那么根本就不可能存在符合要求的袋子，返回0即可；否则，从小到大选择，当选择到 a1,a2,...,ak-1 时满足要求，而再选择 ak 时却不满足，那么之后的数必然也无法满足，此时就不必再向后搜索，这就是剪枝的思想。具体的思路请参考如下代码：<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int GetLuckyBag(vector<int>& bag, size_t pos, long long  sum, long long product) {
	size_t size = bag.size();
	int count = 0;

	for (size_t i = pos; i < size; ++i) {
		//将当前元素加入组合中
		sum += bag[i];
		product *= bag[i];

		if (sum > product) //如果当前组合的和大于积，那么符合要求，此时继续往后搜索，看是否还有符合要求的组合
			count += 1 + GetLuckyBag(bag, i + 1, sum, product);
		else //如果当前组合的和不大于积，那么不符合要求，并且后面也不可能有符合要求的组合了，所以不再往后搜索（剪枝）
			break;

		//将当前元素从组合中除去，继续往后搜索
		sum -= bag[i];
		product /= bag[i];
		for (; i < size - 1 && bag[i] == bag[i + 1]; ++i); //此时往后搜索时，需跳过重复元素
	}

	return count;
}

int main() {
	size_t n = 0;
	cin >> n;

	vector<int> bag;
	bag.resize(n);
	for (size_t i = 0; i < n; ++i)
		cin >> bag[i];

	sort(bag.begin(), bag.end()); //升序排序

	if (bag[0] != 1) //如果袋子中没有1，那么就不可能满足和大于积的要求
		cout << 0 << endl;
	else //否则，从第二个位置开始遍历
		cout << GetLuckyBag(bag, 1, 1, 1) << endl;

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 上述代码中，在将当前元素从组合中除去后继续向后搜索时，我们一定要记得跳过重复的元素，否则结果会出错。<br>
