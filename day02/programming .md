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

&#160; &#160; &#160; &#160; 在原字符串中，从后往前寻找第一个空格，当遇到空格时，取出空格后面的单词，然后缩小范围继续寻找空格。按照这种方法，将单词逐个取出，并同时和之前的单词拼接成一个新字符串，从而作为结果输出。<br>

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
            size_t begin = str.rfind(' ', end-1); //从后往前找第一个空格
            if(begin == std::string::npos)
             	break;
            tmp = str.substr(begin+1, end-begin-1); //将单词逐个取出来
            ret = ret + tmp + " "; //和之前的单词进行拼接
            end = begin; //缩小字符串范围
        }
         
        tmp = str.substr(0, end); //将最后一个单词取出来
        ret += tmp; //拼接
         
        cout << ret << endl;
    }
     
    return 0;
}
```

- **【解题思路二】**<br>

&#160; &#160; &#160; &#160; 先将整个字符串逆置过来，再遍历字符串，找出每个单词，并对单词进行逆置。

- **【代码】**<br>
```c++
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

int main() {
	string str;
	getline(cin, str);
	
	reverse(str.begin(), str.end()); //逆置原字符串
	
	auto begin = str.begin();
	while (begin != str.end()) {
		auto end = begin;
		while (end !=str.end() && *end != ' ')
			end++;
		reverse(begin, end); //逆置单词
		
		if (end != str.end())
			begin = end + 1;
		else
			break;
	}
	cout << str << endl;
	
	return 0;
}
```

- **【解题思路三】**<br>

&#160; &#160; &#160; &#160; 第三种思路是一个比较讨巧的思路，直接利用 `cin >> str` 接收字符串输入，由于 `cin` 遇到空格就结束了，所以通过这种方法自然就将字符串中的每个单词分割出来，最后再将每次分割出来的的单词拼接到之前单词的前面即可。<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <string>
 
using namespace std;
 
int main() {
    string str1, str2;
    cin >> str2; //先将第一个单词分割出来
    while(cin >> str1) {
        str2 = str1 + " " + str2; //边分割边拼接
    }
    cout << str2 << endl;
    
    return 0;
}
```
