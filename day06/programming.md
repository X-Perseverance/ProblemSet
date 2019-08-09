### 1. 标题：[不要二](https://www.nowcoder.com/practice/1183548cd48446b38da501e58d5944eb?tpId=85&&tqId=29840&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 

- **【代码】**
```c++
#include <iostream>
 
using namespace std;
 
int main() {
    int m=0, h=0, ret=0;
    int arr[1000][1000]={0};
    cin >> m >> h;
     
    for(int i=0; i<h; ++i) {
        for(int j=0; j<m; ++j) {
            if(arr[i][j] == 0) {
                // 如果该坐标值为0，表示可以放蛋糕，块数累加；
                // 然后，把与当前坐标欧几里得距离为2的坐标值置为-1，表示不能放蛋糕
                // 与当前坐标欧几里得距离为2的坐标只能在水平和垂直方向
                ret++;
                if(i+2 < h) // 垂直方向
                    arr[i+2][j] = -1;
                if(j+2 < m) // 水平方向
                    arr[i][j+2] = -1;
            }
        }
    }
     
    cout << ret << endl;
     
    return 0;
}
```

### 2. 标题：[把字符串转换成整数](https://www.nowcoder.com/practice/1277c681251b4372bdef344468e4f26e?tpId=13&&tqId=11202&rp=6&ru=/activity/oj&qru=/ta/coding-interviews/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 

- **【代码】**
```c++
class Solution {
public:
    int StrToInt(string str) {
        size_t size = str.size();
        if(size == 0)
            return 0;
         
        int ret = 0;
        int flag = (str[0] == '-') ? -1 : 1; //判断正负号
        size_t i = (str[0] == '-' || str[0] == '+') ? 1 : 0; //若第一个字符为正负号，则从第二个字符开始遍历；否则，从第一个字符开始遍历
         
        for( ; i<size; ++i) {
            if(!isdigit(str[i]))
                return 0;
            ret = (ret<<1) + (ret<<3) + (str[i]&0xf); //ret=ret*10+str[i]-'0';
        }
         
        return ret*flag;
    }
};
```
