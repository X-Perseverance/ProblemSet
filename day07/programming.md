### 1. 标题：[Fibonacci数列](https://www.nowcoder.com/practice/18ecd0ecf5ef4fe9ba3f17f8d00d2d66?tpId=85&&tqId=29846&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**

- **【代码】**
```c ++
#include <iostream>
 
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
         
        if(n - sum > 0)
            left = n - sum;
        else {
            right = sum - n;
            break;
        }
    }
     
    cout << min(left, right) << endl;
     
    return 0;
}
```

### 2. 标题：[合法括号序列判断](https://www.nowcoder.com/practice/d8acfa0619814b2d98f12c071aef20d4?tpId=8&&tqId=11039&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking)
- **【解题思路】**

- **【代码】**
```c ++
class Parenthesis {
public:
    bool chkParenthesis(string A, int n) {
        int flag = 0;
        for(size_t i=0; i<n; ++i) {
            if(A[i] == '(')
                ++flag;
            else if(A[i] == ')' && flag != 0)
                --flag;
            else if(A[i] == ')' && flag == 0)
                return false;
        }
        if(flag == 0)
            return true;
        return false;
    }
};
```
