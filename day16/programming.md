### 1. 标题：[完全数计算](https://www.nowcoder.com/practice/7299c12e6abb437c87ad3e712383ff84?tpId=37&&tqId=21279&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以先直接计算 n 以内（含n）每一个数的约数和，再进一步判断该数是否为完全数，若是累加即可。<br>

- **【代码】**
```c ++
#include <iostream>
#include <cmath>

using namespace std;

int Count(int n) {
	if (n <= 0 || n > 500000)
		return -1;

	int count = 0;
	for (int i = 6; i <= n; ++i) { //从6遍历到n（因为1~5不是完全数，所以不用遍历）
		int sum = 0;
		for (int j = 2; j <= sqrt(i); ++j) { //计算每个数的约数和（不包括1和自身）
			if (i%j == 0) {
				if (i / j == j) //两个约数相同，则只加一个
					sum += j;
				else //两个约数不同，则都要累加
					sum += j + i / j;
			}
		}
		if (sum + 1 == i) //若上面的约数和加一等于该数本身，那么这个数就是一个完全数
			++count;
	}

	return count;
}

int main() {
	int num = 0;
	
	while (cin >> num)
		cout << Count(num) << endl;

	return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 在上述代码中，一定要考虑两个约数是否相等的情况，否则会得到错误结果。<br>

### 2. 标题：[扑克牌大小](https://www.nowcoder.com/practice/0a92c75f5d6b4db28fcfa3e65e5c9b3f?tpId=49&&tqId=29277&rp=1&ru=/activity/oj&qru=/ta/2016test/question-ranking)
- **【题目解析】**<br>

&#160; &#160; &#160; &#160; 对于本题的输入来说，两份手牌的类型都只是 **个子、对子、三个、顺子、炸弹以及对王** 之中的一种，不可能有其他情况。<br>

- **【解题思路】**<br>

&#160; &#160; &#160; &#160; （1）首先当输入的手牌中有对王时，我们就可以直接输出，因为对王是最大的手牌；<br>
&#160; &#160; &#160; &#160; （2）由于输入的两份手牌都是合法的，所以我们可以通过手牌数来确定手牌的类型。对于类型相同的两份手牌，我们比较各自最小的牌就可以确定出大小，而题目中又说明顺子已经从小到大排列，所以比较每份手牌中的第一张牌即可；对于类型不同的两份手牌，只有是炸弹或对王才可以和其他类型的牌进行比较（除此之外的其他类型手牌两两是无法比较大小的），由于在第一步时我们已将对王排除过，所以此时只需考虑有炸弹的情况即可，而在这种情况下，炸弹是最大的。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

int main() {
	string str;
	
	while (getline(cin, str)) {
		if (str.find("joker JOKER") != std::string::npos) //如果手牌有对王，则直接输出，因为对王最大
			cout << "joker JOKER" << endl;
		else {
			//通过截取获取到两份手牌
			size_t pos = str.find('-');
			string str1 = str.substr(0, pos);
			string str2 = str.substr(pos + 1);

			//统计两份手牌各自的空格数，进而可求出牌数
			int count1 = count(str1.begin(), str1.end(), ' ');
			int count2 = count(str2.begin(), str2.end(), ' ');

			//获取到两份手牌各自的第一张牌，也是各自最小的牌
			string firstCard1 = str1.substr(0, 1);
			string firstCard2 = str2.substr(0, 1);

			//已排序手牌，为后面比较手牌大小做标准
			string sortString = "345678910JQKA2jokerJOKER";

			if (count1 == count2) { //如果两份手牌牌数相等，则表示手牌类型相同，所以比较各自最小牌的大小即可
				if (sortString.find(firstCard1) > sortString.find(firstCard2))
					cout << str1 << endl;
				else
					cout << str2 << endl;
			}
			else { //如果两份手牌牌数不相等，则表示手牌类型不同。但若此时有一份手牌中有炸弹（即3个空格，4张牌），则炸弹大；而对于其他不同类型的手牌，是无法比较大小的，所以输出错误
				if (count1 == 3)
					cout << str1 << endl;
				else if (count2 == 3)
					cout << str2 << endl;
				else
					cout << "ERROR" << endl;
			}
		}
	}

	return 0;
}
```
