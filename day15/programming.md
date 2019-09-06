### 1. 标题：[查找输入整数二进制中1的个数](https://www.nowcoder.com/practice/1b46eb4cf3fa49b9965ac3c2c1caf5ad?tpId=37&&tqId=21285&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>
- [ ] 传统方法：<br>

> &#160; &#160; &#160; &#160; 本题的要求是计算一个整数 num 二进制表示中 1 的个数，那么我们可以通过 `num & (1 << i)` 获取到 num 第 i 位的二进制值，当 i 从 0 变化到 31时，就可以获取到整数 num 的每一位二进制值，进而就能计算出 1 的个数。但是这种方法对任何一个整数来说都必须循环 32 次，效率太低，为了提高代码执行效率，我们可以使用下面这种非常巧妙的方法，它循环的次数仅仅是这个整数二进制表示中 1 的个数。<br>

- [x] 高级方法：<br>

> &#160; &#160; &#160; &#160; 对任意一个整数来说，只要它不为 0 ，那么它的二进制表示中必定有 1，所以我们试想：如果有一种运算每次都能将这个整数的二进制表示中的一个 1 变为 0，那么当这个整数为 0 时，就计算出了 1 的个数。<br>
> &#160; &#160; &#160; &#160; 在学习C语言的过程中，我们可能遇到过这样一道题：如何判断一个整数 num 是不是 2 的 n 次方？这道题仅用一句代码即可求解，那就是 `return (num &= num-1)==0;`。我们知道一个整数要是 2 的 n 次方，那么它的二进制表示中仅有一个 1，而 `num &= num-1` 会将 num 二进制表示中最右边的 1 变为 0，所以若代码执行后，num 变为 0，那就证明 num 就是 2 的 n 次方，否则不是。<br>
> &#160; &#160; &#160; &#160; 借鉴上述问题，我们会发现 `num &= num-1` 这条语句正是我们需要的那种运算方法，所以我们可以写出下面所示代码：<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

void findNumberOf1(int num) {
	int count = 0;
	while (num) {
		count++; //统计 1 的个数
		num &= num - 1; //将 num 二进制表示中最右边的 1 变为 0
	}
	cout << count << endl;
}

int main() {
	int number = 0;
	while (cin >> number)
		findNumberOf1(number);

	return 0;
}
```

### 2. 标题：[手套](https://www.nowcoder.com/practice/365d5722fff640a0b6684391153e58d8?tpId=49&&tqId=29337&rp=1&ru=/activity/oj&qru=/ta/2016test/question-ranking)
- **【解题思路】**<br>
&#160; &#160; &#160; &#160; 假设有一个**非零递增序列** `x1 < x2 < x3 < x4 < ... < xn`，其中每一项都代表一种颜色小球的数量，现在要从这些小球中拿取一些，以保证每一种颜色的小球都能取到，那么我们最少要拿多少？答案就是 `sum(x1,x2,...,xn) - x1 + 1`，只有这样拿才能覆盖到每一种颜色。<br>
&#160; &#160; &#160; &#160; 借鉴上述问题，那么对于本题来说，我们先不考虑某种颜色的左手或右手手套数为 0 的情况，此时只需分别求出左手手套和右手手套各自拿取的最少数量，接着再从这两个数中找出最小数，最终加一即可，意思就是：**在左手手套或右手手套的一边拿取一定数量的手套，而在另一边随便拿取一个就能保证至少有一种颜色的手套匹配，为了最终拿取的数量最少，所以我们要在计划拿取的左手手套或右手手套中选择数量最少的拿**，此时要拿取的手套数记为 `min(leftSum - leftMin + 1, rightSum - rightMin + 1) + 1`；接下来再来考虑某一种颜色的左手或右手手套为 0 的情况，对于这种情况，我们就需要把这些手套累加起来，因为我们必须保证拿取的手套要覆盖到每一种颜色，此时要拿取的手套数记为 `count`。<br>
&#160; &#160; &#160; &#160; 综上所述，最终拿取的手套数就是 `count + min(leftSum - leftMin + 1, rightSum - rightMin + 1) + 1`。<br>

- **【代码】**
```c ++
class Gloves {
public:
	int findMinimum(int n, vector<int> left, vector<int> right) {
		int count = 0;
		int leftSum = 0, leftMin = INT_MAX;
		int rightSum = 0, rightMin = INT_MAX;

		for (int i = 0; i < n; ++i) { //某一种颜色的左手或右手手套为 0 的情况
			if (left[i] * right[i] == 0)
				count += left[i] + right[i];
			else { //不为 0 的情况
				leftSum += left[i];
				rightSum += right[i];
				leftMin = min(leftMin, left[i]);
				rightMin = min(rightMin, right[i]);
			}
		}

		return count + min(leftSum - leftMin + 1, rightSum - rightMin + 1) + 1;
	}
};
```
