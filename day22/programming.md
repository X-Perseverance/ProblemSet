### 1. 标题：[小易的升级之路](https://www.nowcoder.com/practice/fe6c73cb899c4fe1bdd773f8d3b42c3d?tpId=49&&tqId=29329&rp=1&ru=/activity/oj&qru=/ta/2016test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题能力值的累加分两种情况，一种是直接累加 b[i] ，一种是累加当前能力值 a 与 b[i] 的最大公约数，而最大公约数可以通过碾转相除法求得。<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>

using namespace std;

int GCD(int x, int y) //利用辗转相除法求最大公约数
{
	int temp = 0;
	while (temp = x % y) {
		x = y;
		y = temp;
	}
	return y;
}

int main()
{
	int n = 0, a = 0;

	while (cin >> n >> a) {
		vector<int> b(n, 0);

		for (int i = 0; i < n; ++i)
			cin >> b[i];

		for (int i = 0; i < n; ++i) {
			if (b[i] > a)
				a += GCD(a, b[i]);
			else
				a += b[i];
		}

		cout << a << endl;
	}

	return 0;
}
```

### 2. 标题：[找出字符串中第一个只出现一次的字符](https://www.nowcoder.com/practice/e896d0f82f1246a3aa7b232ce38029d4?tpId=37&&tqId=21282&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题我们可以定义一个大小为 256 的数组，这样数组的每一个下标就刚好对应每一个字符的 ASCII 码值，接着使用这个数组依次统计字符串中每一个字符出现的次数，最后再从数组中找出第一个只出现一次的字符即可。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string str;

	while (cin >> str) {
		int hashTable[256] = { 0 };
		size_t i = 0;
		size_t size = str.size();

		for (i = 0; i < size; ++i) //使用数组依次统计字符串中每一个字符出现的次数
			hashTable[str[i]]++;

		for (i = 0; i < size; ++i) { //找出第一个只出现一次的字符
			if (hashTable[str[i]] == 1) {
				cout << str[i] << endl;
				break;
			}
		}
		if (i == size) //如果不存在输出-1
			cout << -1 << endl;
	}

	return 0;
}
```
