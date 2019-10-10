### 1. 标题：[年终奖](https://www.nowcoder.com/practice/72a99e28381a407991f2c96d8cb238ab?tpId=49&&tqId=29305&rp=1&ru=/activity/oj&qru=/ta/2016test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以采用动态规划的思想来解题。由于小东每次只能向下或者向右移动一步，所以他在每一个格子上时能获得的最大价值为 **max(在左边格子时能获得的最大价值, 在上边格子时能获得的最大价值) + 当前格子价值** ，当然第一行和第一列的格子由于没有上边格子或左边格子也就无法直接计算，但是我们可以在棋盘的上边和左边多加一行或一列，并设置这些格子的价值都为0，以作为初值来使用。<br>
&#160; &#160; &#160; &#160; 所以，我们可以定义一个二维数组 `maxValue[length+1][wideth+1]` ，其中 `maxValue[i][j]` 代表从棋盘左上角到达 (i,j) 这个格子时所能获得的最大价值，那么从上面的分析可以得到：`maxValue[i][j] = max(maxValue[i-1][j], maxValue[i][j-1]) + board[i-1][j-1]` ，由于第一行和第一列是作为初值使用，所以 i 和 j 从1开始。当遍历完整个棋盘时，`maxValue[length][wideth]` 就是从棋盘左上角到达右下角时所能获得的最大价值。<br>

- **【代码】**
``` c ++
class Bonus {
public:
	int getMost(vector<vector<int>> board) {
		int length = board.size();
		int wideth = board[0].size();
		vector<vector<int>> maxValue(length + 1, vector<int>(wideth + 1, 0));

		for (int i = 1; i <= length; ++i) {
			for (int j = 1; j <= wideth; ++j) {
				maxValue[i][j] = max(maxValue[i - 1][j], maxValue[i][j - 1]) + board[i - 1][j - 1];
			}
		}

		return maxValue[length][wideth];
	}
};
```

### 2. 标题：[迷宫问题](https://www.nowcoder.com/practice/cf24906056f4488c9ddb132f317e03bc?tpId=37&&tqId=21266&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以采用回溯法的思想来解题，具体步骤如下：<br>

> （1）首先，将当前位置加入到所走的路径中去，并对该位置进行标记以表示已走过；<br>
> （2）接着，判断当前位置是否为出口，如果为出口，则更新最短路径；如果不是，则依次判断当前位置的上、下、左、右四个方向是否可走，可走的话则走该方向的下一个位置，即跳转到步骤（1）；<br>
> （3）最后，将当前位置从所走路径中删除，并撤销标记以表示可走；<br>

&#160; &#160; &#160; &#160; 当迷宫中每一个位置的四个方向都走过之后，就可以找出最短的路径。<br>

- **【代码】**
``` c ++
#include <iostream>
#include <vector>

using namespace std;

struct pos { //位置坐标
	int x;
	int y;
};

int m = 0, n = 0; //迷宫的行和列
vector<vector<int>> maze; //迷宫
vector<struct pos> curPath; //当前路径
vector<struct pos> shortPath; //最短路径

void FindPath(int x, int y)
{
	maze[x][y] = 1; //将当前位置进行标记，表示已经走过
	curPath.push_back({ x,y }); //将当前位置插入到当前路径中去

	if (x == m - 1 && y == n - 1) { //判断是否到达出口
		if (shortPath.empty() || curPath.size() < shortPath.size()) //若到达出口，则更新最短路径
			shortPath = curPath;
	}
	else {
		if (x - 1 >= 0 && maze[x - 1][y] == 0) //向上探索路径
			FindPath(x - 1, y);
		if (x + 1 < m && maze[x + 1][y] == 0) //向下探索路径
			FindPath(x + 1, y);
		if (y - 1 >= 0 && maze[x][y - 1] == 0) //向左探索路径
			FindPath(x, y - 1);
		if (y + 1 < n && maze[x][y + 1] == 0) //向右探索路径
			FindPath(x, y + 1);
	}

	maze[x][y] = 0; //撤销对当前位置的标记
	curPath.pop_back(); //将当前位置从当前路径中删除
}

int main()
{
	while (cin >> m >> n) {
		// 第一步：初始化迷宫
		maze = vector<vector<int>>(m, vector<int>(n, 0));
		for (int i = 0; i < m; ++i) {
			for (int j = 0; j < n; ++j) {
				cin >> maze[i][j];
			}
		}

		// 第二步：清空路径
		curPath.clear();
		shortPath.clear();

		// 第三步：寻找最短路径
		FindPath(0, 0);

		// 第四步：输出最短路径
		for (size_t i = 0; i < shortPath.size(); ++i) {
			cout << "(" << shortPath[i].x << "," << shortPath[i].y << ")" << endl;
		}
	}

	return 0;
}
```
