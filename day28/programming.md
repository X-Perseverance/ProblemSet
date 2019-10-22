### 1. 标题：[奇数位上都是奇数或者偶数位上都是偶数](https://www.nowcoder.com/questionTerminal/b89b14a3b5a94e438b518311c5156366)
- **【解题思路】**

　　在偶数位上寻找非偶数，在奇数位上寻找非奇数，找到后将两个数字进行位置互换即可。<br>

- **【代码】**
```c ++
class Solution {
public:
	void oddInOddEvenInEven(vector<int>& arr, int len) {
		int i = 0, j = 1;
		while(i < len && j < len){
			while(i < len && (arr[i] & 1) == 0) //在偶数位上找非偶数
				i += 2;
			while(j < len && (arr[j] & 1) == 1) //在奇数位上找非奇数
				j += 2;
			if(i < len && j < len) //找到后交换两个数
				swap(arr[i], arr[j]);
		}
	}
};
```

### 2. 标题：[猴子分桃](https://www.nowcoder.com/questionTerminal/480d2b484e1f43af8ea8434770811b4a)
- **【解题思路】**

　　

- **【代码】**
```c ++
#include <iostream>
#include <cmath>

using namespace std;

int main() {
	int n = 0;

	while (cin >> n) {
		if (n == 0)
			break;

		long total = pow(5, n) - 4;
		long left = pow(4, n) + n - 4;
		cout << total << " " << left << endl;
	}

	return 0;
}
```
