### 1. 标题：[Fibonacci数列](https://www.nowcoder.com/practice/18ecd0ecf5ef4fe9ba3f17f8d00d2d66?tpId=85&&tqId=29846&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以先找到距离N最近的两个Fibonacci数，这两个数分别取自距离N最近的左边数L和右边数R，然后通过min(N - L, R - N)找到最小步数即可。<br>

- **【代码】**
```c ++
#include <iostream>
#inlcude <algorithm>
 
using namespace std;
 
int main() {
    int n=0;
    cin >> n;
     
    int num1=0, num2=1, sum=0;
    int left=0, right=0;
    while(1) {
        sum = num1 + num2;
        num1 = num2;
        num2 = sum;
         
        if(n - sum > 0) //找到比n小且距离n最近的Fibonacci数，求出距离
            left = n - sum;
        else { //找到比n大且距离n最近的Fibonacci数，求出距离
            right = sum - n;
            break;
        }
    }
     
    cout << min(left, right) << endl; //取n和左右Fibonacci数距离的最小值
     
    return 0;
}
```

### 2. 标题：[合法括号序列判断](https://www.nowcoder.com/practice/d8acfa0619814b2d98f12c071aef20d4?tpId=8&&tqId=11039&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 一对合法的括号由左括号和右括号组成，所以一个合法的括号序列必须满足以下条件：<br>

> - 每一个左括号都有一个位于其后的右括号与之匹配<br>
> - 每一个右括号都有一个位于其前的左括号与之匹配<br>

&#160; &#160; &#160; &#160; 从上述来看，我们可以先设置一个计数器count，表示还未匹配的左括号数，接着从头遍历字符串，若遇到左括号则count++，说明有左括号还未匹配；若遇到右括号并且之前还有左括号未匹配（即count != 0），则count--，说明已成功匹配一对括号；若遇到右括号并且之前所有左括号都已成功匹配或者没有左括号出现（即count == 0），则直接返回false，因为它不满足条件二。当遍历完成后，若所有左括号都已成功匹配或者没有左括号出现（即count == 0），则返回true，否则说明还有左括号未能匹配，此时返回false，因为它不满足条件一。<br>

- **【代码】**
```c ++
bool chkParenthesis(string A, int n) {
	int count = 0;
	for (size_t i = 0; i < n; ++i) {
		if (A[i] == '(')
			++count;
		else if (A[i] == ')' && count != 0)
			--count;
		else if (A[i] == ')' && count == 0)
			return false;
	}
	if (count == 0)
		return true;
	return false;
}
```
