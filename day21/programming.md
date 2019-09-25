### 1. 标题：[洗牌](https://www.nowcoder.com/practice/5a0a2c7e431e4fbbbb1ff32ac6e8dfa0?tpId=85&&tqId=29848&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题就是一个模拟洗牌的例子，它先将原始牌组均分为两组，接着从两组牌的最后一张牌开始交叉排列，交叉完毕后就是一次洗牌后的结果，而题目要求我们洗牌k次，所以重复以上过程k次即可。由此说明我们只要能找出一次洗牌的规律就可以解题，这也是本题的关键所在。<br>
&#160; &#160; &#160; &#160; 在每一次洗牌的过程中，我们每读一张牌就能根据它当前所在的位置找出它下一次出现的位置，具体分为以下两种情况：（ i 从 0 到 n-1 ）<br>
&#160; &#160; &#160; &#160; （1）**下标在 [0, n-1] 之间，表示当前牌位于左手，那么它下次所在的位置是 `2*i`**<br>
&#160; &#160; &#160; &#160; （2）**下标在 [n, 2\*n-1] 之间，表示当前牌位于右手，那么它下次所在的位置是 `2*i+1`**<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>

using namespace std;

int main()
{
	int T = 0, n = 0, k = 0;

	cin >> T;
	while (T--) {
		cin >> n >> k;
		int size = 2 * n;
		vector<int> array(size, 0);

		//第一步：输入原始牌组
		for (int i = 0; i < size; ++i)
			cin >> array[i];
		
		//第二步：洗k次牌
		while (k--) {
			vector<int> temp(array.begin(), array.end()); //保存每一次洗牌前的牌组
			for (int i = 0; i < n; ++i) {
				array[2 * i] = temp[i]; //下标在 [0, n-1] 之间，表示当前牌位于左手，那么它下次所在的位置是 2*i
				array[2 * i + 1] = temp[n + i]; //下标在 [n, 2*n-1] 之间，表示当前牌位于右手，那么它下次所在的位置是 2*i+1
			}
		}

		//第三步：输出洗牌后的牌组
		for (int i = 0; i < size -1; ++i)
			cout << array[i] << " ";
		cout << array[size - 1] << endl;
	}

	return 0;
}
```

### 2. 标题：[MP3光标位置](https://www.nowcoder.com/practice/eaf5b886bd6645dd9cfb5406f3753e15?tpId=37&&tqId=21287&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题分为歌曲总数不超过4和超过4这两种情况，对每一种情况再分情况讨论，进行移动即可，具体思路见代码部分。<br>

- **【代码】**
```c ++
#include <iostream>
#include <string>

using namespace std;

int main() {
	int n = 0; //歌曲总数
	string order; //命令

	while (cin >> n >> order) {
		int firstSong = 1; //当前页面第一首歌曲位置
		int currentCursor = 1; //当前光标位置

		if (n <= 4) { //当歌曲总数不超过4时，firstSong始终不变
			for (size_t i = 0; i < order.size(); ++i) {
				if (order[i] == 'U') {
					if (currentCursor == 1) //光标在第一首歌曲上时，按Up键光标挪到最后一首歌曲
						currentCursor = n;
					else //其他情况下，按Up键光标挪到上一首歌曲
						currentCursor--;
				}
				else if (order[i] == 'D') {
					if (currentCursor == n) //光标在最后一首歌曲时，按Down键光标挪到第一首歌曲
						currentCursor = 1;
					else //其他情况下，按Down键光标挪到下一首歌曲
						currentCursor++;
				}
			}

			for (int i = 1; i < n; ++i) //输出当前列表
				cout << i << " ";
			cout << n << endl;
			cout << currentCursor << endl; //输出当前选中歌曲
		}
		else { //当歌曲总数超过4时
			for (size_t i = 0; i < order.size(); ++i) {
				if (order[i] == 'U') {
					if (firstSong == 1 && currentCursor == 1) { //特殊翻页
						currentCursor = n;
						firstSong = n - 3;
					}
					else if (firstSong != 1 && currentCursor == firstSong) { //一般翻页
						currentCursor--;
						firstSong--;
					}
					else //其他情况
						currentCursor--;
				}
				else if (order[i] == 'D') {
					if (firstSong == n - 3 && currentCursor == n) { //特殊翻页
						currentCursor = 1;
						firstSong = 1;
					}
					else if (firstSong != n - 3 && currentCursor == firstSong + 3) { //一般翻页
						currentCursor++;
						firstSong++;
					}
					else //其他情况
						currentCursor++;
				}
			}

			for (int i = firstSong; i < firstSong + 3; ++i) //输出当前列表
				cout << i << " ";
			cout << firstSong + 3 << endl;
			cout << currentCursor << endl; //输出当前选中歌曲
		}
	}

	return 0;
}
```
