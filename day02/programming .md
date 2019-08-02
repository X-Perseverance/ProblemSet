### 1. 标题：[排序子序列](https://www.nowcoder.com/questionTerminal/2d3f6ddd82da445d804c95db22dcc471?orderByHotValue=1&page=1&onlyReference=false)
- **【题目解析】**<br>
&#160; &#160; &#160; &#160; 本题要求解的是排序子序列，排序子序列为非递增或者非递减，很多同学在这个非递增、非递减问题上很纠结，注意：非递减就是a[i]<=a[i+1]，递减就是a[i]>a[i+1]，非递增就是a[i]>=a[i+1]，递增就是a[i]<a[i+1]。其实这个不理解网上搜一下就理解了。<br>

- **【解题思路】**<br>
&#160; &#160; &#160; &#160; 通过上面理解了排序子序列，如果我们把这里值画到一个坐标图里面，本质就是去找这里图里面的波峰和波谷的个数，再加一。<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <vector>
 
using namespace std;
 
int main() {
    int n = 0;
     
    while(cin >> n) {
        vector<int> v;
        v.resize(n);
         
        for(size_t i=0; i<n; ++i)
            cin >> v[i];
         
        int count = 1;
        int flag = 0;
        for(size_t i=1; i<n; ++i) {
            if(v[i] > v[i-1]) {
                if(flag == 0) {
                    flag = 1;
                }
                else if(flag == -1) {
                    flag = 0;
                    ++count;
                }
            }
            else if(v[i] < v[i-1]) {
                if(flag == 0) {
                    flag = -1;
                }
                else if(flag == 1) {
                    flag = 0;
                    ++count;
                }
            }
        }
         
        cout << count << endl;
    }
     
    return 0;
}
```

### 2. 标题：[倒置字符串](https://www.nowcoder.com/practice/ee5de2e7c45a46a090c1ced2fdc62355?tpId=85&&tqId=29867&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路一】**<br>
&#160; &#160; &#160; &#160; 先将整个字符串逆置过来，再遍历字符串，找出每个单词，对单词逆置。这里我们使用了stl算法中的reverse，所以这里使用迭代器遍历string。<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <string>
 
using namespace std;
 
int main() {
    string str;
     
    while(getline(cin, str)) {
        string tmp, ret;
        size_t end = str.size();
        while(1) {
            size_t begin = str.rfind(' ', end-1);
            if(begin == std::string::npos)
              break;
            tmp = str.substr(begin+1, end-begin-1);
            ret = ret + tmp + ' ';
            end = begin;
        }
         
        tmp = str.substr(0, end);
        ret += tmp;
         
        cout << ret << endl;
    }
     
    return 0;
}
```

- **【解题思路二】**<br>
&#160; &#160; &#160; &#160; 第二思路是一个比较讨巧的思路，直接利用cin>>s接收输入，遇到空格就结束了，自然就分割开了每个单词，其次将每次接收到的单词拼接到之前串的前面就逆置过来了<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <string>

using namespace std;

int main() {
	string s1, s2;
	cin >> s2;
	while (cin >> s1)
	s2 = s1 + " " + s2;
	cout << s2 << endl;
	
	return 0;
}
```
