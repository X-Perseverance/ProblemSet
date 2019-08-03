### 1. 标题：[排序子序列](https://www.nowcoder.com/questionTerminal/2d3f6ddd82da445d804c95db22dcc471?orderByHotValue=1&page=1&onlyReference=false)
- **【题目解析】**<br>

&#160; &#160; &#160; &#160; 本题需要求解的是一个数组可以被划分为多少个排序子序列，而排序子序列指的就是那些`非递增`或`非递减`的子序列。所以对这道题而言，其突破点就是找出这些排序子序列之间的界线，也就是那些排序规则改变的过渡点。<br>

- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 通过上面的解析，我们知道问题的关键在于找出那些过渡点，而那些过渡点都拥有一个很明显的特点，就是它们`与前一个数据的大小关系违背了上一个子序列的排序规则`。比如，现有一组数据 `1 1 5 2 5`，我们可以直接看出答案为2，即 `1 1 5` 和 `2 5` 这两个子序列，划分的界线就是 `2`，在 2 之前的子序列是一个非递减序列，而 2 与前一个数据 5 呈递减关系，它违背了上个子序列的排序规则，所以不能与上一个序列划分在一起，而是作为下一个子序列的开始。<br>
&#160; &#160; &#160; &#160; 知道了这个特点，解决问题就容易多了。首先，我们从数组第二个元素开始遍历，每个元素都和上一个元素作比较，若它们两者的关系没有违背上一个子序列的排序规则，则继续往后遍历；若违背了，则开始一个新的序列，划分计数加一，直到遍历完为止。<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <vector>

using namespace std;

int main() {
	int n = 0;

	while (cin >> n) {
		vector<int> v;
		v.resize(n);

		for (size_t i = 0; i < n; ++i)
			cin >> v[i];

		int count = 1; //划分计数值
		int flag = 0;  //排序规则：1代指非递减，-1代指非递增，0代表未知规则(因为当序列只有一个数据时，还不能确定其规则)

		for (size_t i = 1; i < n; ++i) { //从数组第二个元素开始遍历

			//情况一：当前元素大于前一个元素
			//	（1）若上一个序列还是未知规则，则将当前元素加入该序列，并设置排序规则为非递减；
			//	（2）若上一个序列是非递增序列，则当前元素违背了其规则，不该划分其中，应重新开始一个子序列，此时排序规则未知，划分计数加一；
			//	（3）若上一个序列是非递减序列，则当前元素正好符合其规则，应划分为一组，继续往后遍历。
			if (v[i] > v[i - 1]) {				
				if (flag == 0) {
					flag = 1;
				}
				else if (flag == -1) {
					flag = 0;
					++count;
				}
			}

			//情况二：当前元素小于前一个元素
			//	（1）若上一个序列还是未知规则，则将当前元素加入该序列，并设置排序规则为非递增
			//	（2）若上一个序列是非递减序列，则当前元素违背了其规则，不该划分其中，应重新开始一个子序列，此时排序规则未知，划分计数加一；
			//	（3）若上一个序列是非递增序列，则当前元素正好符合其规则，应划分为一组，继续往后遍历。
			else if (v[i] < v[i - 1]) {
				if (flag == 0) {
					flag = -1;
				}
				else if (flag == 1) {
					flag = 0;
					++count;
				}
			}

			//情况三：当前元素等于前一个元素
			//	对于这种情况，由于当前元素并没有影响到上一个序列的排序规则，所以可将其划分为一组，继续往后遍历即可。
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
