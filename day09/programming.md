### 1. 标题：[井字棋](https://www.nowcoder.com/practice/e1bb714eb9924188a0d5a6df2216a3d1?tpId=8&&tqId=11055&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 相信大家对井字棋都不陌生，其获胜的方法就是有相同的三个点连成一线，所以对于本题可分四种情况来表示当前玩家获胜：（1）任意一行的和为3；（2）任意一列的和为3；（3）主对角线的和为3；（4）副对角线的和为3。以下代码对井字棋进行了扩展，适用于 N * N 的棋盘。<br>

- **【代码】**
```c ++
bool checkWon(vector<vector<int> > board) {
	int len = board.size();
	int sum = 0;

	for (int i = 0; i < len; ++i) { //判断每一行的和是否为len
		sum = 0;
		for (int j = 0; j < len; ++j) {
			sum += board[i][j];
		}
		if (sum == len)
			return true;
	}

	for (int i = 0; i < len; ++i) { //判断每一列的和是否为len
		sum = 0;
		for (int j = 0; j < len; ++j) {
			sum += board[j][i];
		}
		if (sum == len)
			return true;
	}

	sum = 0;  //判断主对角线的和是否为len
	for (int i = 0; i < len; ++i) {
		sum += board[i][i];
	}
	if (sum == len)
		return true;

	sum = 0;  //判断副对角线的和是否为len
	for (int i = 0; i < len; ++i) {
		sum += board[i][len - 1 - i];
	}
	if (sum == len)
		return true;

	return false;
}
```

### 2. 标题：[密码强度等级](https://www.nowcoder.com/practice/52d382c2a7164767bca2064c1c9d5361?tpId=37&&tqId=21310&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题的解决思路很简单，先计算出每一部分的得分，再根据总得分划分安全等级即可。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>

using namespace std;

int GetScore1(size_t size) { //密码长度
	if (size <= 4)
		return 5;
	else if (size >= 8)
		return 25;
	else
		return 10;
}

int GetScore2(string str, size_t size) { //字母
	int lowercase = 0, uppercase = 0;
	for (size_t i = 0; i < size; ++i) {
		if (str[i] >= 65 && str[i] <= 90)
			++uppercase;
		else if (str[i] >= 97 && str[i] <= 122)
			++lowercase;
	}
	if ((lowercase + uppercase) == 0)
		return 0;
	else if (lowercase == size || uppercase == size)
		return 10;
	else if (lowercase > 0 && uppercase > 0)
		return 20;
	return 0;
}

int GetScore3(string str, size_t size) { //数字
	int count = 0;
	for (size_t i = 0; i < size; ++i) {
		if (str[i] - '0' >= 0 && str[i] - '0' <= 9)
			++count;
	}
	if (count == 0)
		return 0;
	else if (count == 1)
		return 10;
	else
		return 20;
}

int GetScore4(string str, size_t size) { //符号
	int count = 0;
	for (size_t i = 0; i < size; ++i) {
		if (!(str[i] >= 65 && str[i] <= 90) && !(str[i] >= 97 && str[i] <= 122) && !(str[i] - '0' >= 0 && str[i] - '0' <= 9))
			count++;
	}
	if (count == 0)
		return 0;
	else if (count == 1)
		return 10;
	else
		return 25;
}

int main() {
	string str;

	while (cin >> str) {
		int score1 = 0, score2 = 0, score3 = 0, score4 = 0, score5 = 0;
		size_t size = str.size();
		
		//第一步：分别计算每一部分的得分
		score1 = GetScore1(size);
		score2 = GetScore2(str, size);
		score3 = GetScore3(str, size);
		score4 = GetScore4(str, size);

		if (score2 == 20 && score3 > 0 && score4 > 0)
			score5 = 5;
		else if (score2 > 0 && score3 > 0 && score4 > 0)
			score5 = 3;
		else if (score2 > 0 && score3 > 0 && score4 == 0)
			score5 = 2;
		
		//第二步：根据总得分划分安全等级
		int sum = score1 + score2 + score3 + score4 + score5;
		if (sum >= 90)
			cout << "VERY_SECURE" << endl;
		else if (sum >= 80)
			cout << "SECURE" << endl;
		else if (sum >= 70)
			cout << "VERY_STRONG" << endl;
		else if (sum >= 60)
			cout << "STRONG" << endl;
		else if (sum >= 50)
			cout << "AVERAGE" << endl;
		else if (sum >= 25)
			cout << "WEAK" << endl;
		else
			cout << "VERY_WEAK" << endl;
	}

	return 0;
}
```
