### 1. 标题：[最近公共祖先](https://www.nowcoder.com/practice/70e00e490b454006976c1fdf47f155d9?tpId=8&&tqId=11017&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 在一棵满二叉树中，子节点与父节点之间的关系为 `root = child / 2`，所以我们可以通过这个关系式来找出每个节点的父节点。由于本题要找出两个节点的最近公共祖先，并且题目中格外说明这里节点本身也可认为是其祖先，也就是说，两个节点中可能有一个节点是另一个的祖先，而作为祖先的那个节点必是两个节点中的较小者，所以我们先找出两个节点中较大者的父节点，将这个父节点和另一个节点比较，如果不相等，则寻找这个父节点和另一个节点的最近公共祖先；如果相等，则该父节点就是最近公共祖先。<br>

- **【代码】**
```c
class LCA {
public:
    int getLCA(int a, int b) {
        while(a != b) {
            if(a > b)
                a /= 2;
            else
                b /= 2;
        }
        return a;
    }
};
```

### 2. 标题：[求最大连续bit数](https://www.nowcoder.com/practice/4b1658fd8ffb4217bc3b7e85a38cfaf2?tpId=37&&tqId=21309&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以直接进行求解，依次获取每一位的二进制值，如果1连续，则计数累加；如果不连续，则从0开始计数。<br>

- **【代码】**
```c
#include <iostream>
#include <algorithm>

using namespace std;

int main()
{
    int number;
    
    while(cin >> number) {
        int currentCount = 0, maxCount = 0;
        
        while(number) {
            if(number & 1) { //若当前位为1，则计数加一，更新最大计数
                ++currentCount;
                maxCount = max(currentCount, maxCount);
            }
            else //若当前位为0，则打破连续，计数置零
                currentCount = 0;
            
            number >>= 1;
        }
        
        cout << maxCount << endl;
    }
    
    return 0;
}
```
