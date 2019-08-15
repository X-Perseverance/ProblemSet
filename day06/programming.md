### 1. 标题：[不要二](https://www.nowcoder.com/practice/1183548cd48446b38da501e58d5944eb?tpId=85&&tqId=29840&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【题目解析】**<br>

&#160; &#160; &#160; &#160; 对于该题，有两个非常关键的地方需要我们注意，一是**任意两块蛋糕的欧几里得距离不能等于2**，在这样一个网格盒子（二维数组）内，由于一个格子只能放一个蛋糕，而与每一个蛋糕相距为2的坐标点只能是在其水平方向和垂直方向，所以这句话的意思就是在每个蛋糕的水平和垂直两个方向相距为2的坐标点不能放蛋糕；另一个是**最多可以放多少块蛋糕**，由于题目要求最多，所以我们就需要考虑一下在什么情况下能放置最多。

- **【解题思路一】**<br>

&#160; &#160; &#160; &#160; 如果该坐标值为0，表示可以放蛋糕，块数累加；然后，把与当前坐标欧几里得距离为2的坐标值置为-1，表示不能放蛋糕；与当前坐标欧几里得距离为2的坐标只能在水平和垂直方向。

- **【代码】**
```c++
#include <iostream>
 
using namespace std;
 
int main() {
    int w = 0, h = 0, ret = 0;
    int arr[1000][1000] = {0};
    cin >> w >> h;
     
    for(int i=0; i<h; ++i) {
        for(int j=0; j<w; ++j) {
            if(arr[i][j] == 0) {
                ret++;
                if(i+2 < h) //垂直方向
                    arr[i+2][j] = -1;
                if(j+2 < w) //水平方向
                    arr[i][j+2] = -1;
            }
        }
    }
     
    cout << ret << endl;
     
    return 0;
}
```

- **【解题思路二】**<br>

&#160; &#160; &#160; &#160; 

- **【代码】**
```c++
#include <iostream>

using namespace std;

int main() {
	int w = 0, h = 0;
	cin >> w >> h;

	int line_12 = w / 4 * 2 + ((w % 4 < 2) ? w % 4 : 2); //第1行或第2行的蛋糕数
	int line_34 = (w - 2) / 4 * 2 + (((w - 2) % 4 < 2) ? (w - 2) % 4 : 2); //第3行或第4行的蛋糕数

	int ret = h / 4 * (line_12 + line_34) * 2; //所有整4行的蛋糕数

	//行数除4有余数的情况：
	if (h % 4 > 0) //至少有第1行
		ret += line_12;
	if (h % 4 > 1) //至少有第1行和第2行
		ret += line_12;
	if (h % 4 > 2) //至少有第1行、第2行和第3行
		ret += line_34;

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
