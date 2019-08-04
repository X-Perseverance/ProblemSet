### 1. 标题：[字符串中找出连续最长的数字串](https://www.nowcoder.com/practice/bd891093881d4ddf9e56e7cc8416562d?tpId=85&&tqId=29864&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 本题可以直接遍历字符串，遍历的同时判断每一个字符是否为数字。若是，则将其累加到一个临时字符串tmp中，以记录每个连续的数字子串；若不是，则连续性遭到破坏，标志着一个连续的数字子串结束了，接着将这个数字子串与前面保存的最长数字串ret进行比较，若更长，则更新ret，然后清空tmp，以备下次记录使用。<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <string>
 
using namespace std;
 
int main() {
    string str, tmp, ret;
    cin >> str;
     
    for(int i=0; i<=str.length(); ++i) {
        if(str[i]>='0' && str[i]<='9') //遇到数字字符则累加到tmp
            tmp += str[i];
        else { //遇到非数字字符，则先判断当前tmp是否为更长的数字串，若是则更新结果ret，接着清空tmp，以备下次遇到新数字子串累加使用
            if(ret.size() < tmp.size())
                ret = tmp;
            tmp.clear();
        }
    }
    
    cout << ret;
     
    return 0;
}
```

- **【坑】**<br>

&#160; &#160; &#160; &#160; 在上述代码中，我们需要格外注意for循环的条件判断语句为 `i<=str.length()`，若不加`=`，则程序出现错误。比如："123a1234"，在不加=的情况下，结果为 123 ，因为当遍历到最后的数字4后并没有机会去更新结果，而是直接跳出循环，将上次保存的数字串输出，所以在这里我们还需要多遍历一次，以避免这种最长数字子串在原字符串最后会出现错误的情况。<br>

### 2. 标题：[n个数里出现次数大于等于n/2的数](https://www.nowcoder.com/practice/eac8c671a0c345b38aa0c07aba40097b?tpId=85&&tqId=29866&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路一】**<br>

&#160; &#160; &#160; &#160; 在这里，我们可以构建一个`unordered_map`来进行解题。首先遍历全部数据，将这些数据和它们各自出现的次数按照key-value的形式一一添加到这个unordered_map中，接着从unordered_map中找出value不小于n/2的key即可。br>

- **【代码】**<br>
```c++
#include <iostream>
#include <vector>
#include <unordered_map>
  
using namespace std;
  
int main() {
    int num=0;
    vector<int> v;
    while( cin >> num ) {
        v.push_back(num);
    }
      
    unordered_map<int, int> m;
    for(auto e : v) { //添加键值对，构建unordered_map
        m[e]++;
    }
      
    for(auto it=m.begin(); it!=m.end(); ++it) { //找出value不小于n/2的key
        if(it->second >= v.size()/2) {
            cout << it->first << endl;
            break;
        }
    }
      
    return 0;
}
```

- **【解题思路二】**<br>

&#160; &#160; &#160; &#160; 为了找出这个过半的数，我们可以用一个变量count记录每个数变化的次数，一个变量temp记录可能过半的数。首先让count=1，temp=v[0]，然后开始往后遍历，遇到和temp相同的数就给count++，否则就count--。如果count变成0，就让temp=v[i]（遍历数组v过程中的当前值），并让count=1，如此遍历一遍，因为仅有一个数过半，所以temp最后肯定存储的是过半的数。<br>

- **【代码】**<br>
```c++
#include <iostream>
#include <vector>

using namespace std;

int main() {
	int num = 0;
	vector<int> v;

	while (cin >> num) {
		v.push_back(num);
	}

	int count = 1;
	int temp = v[0];
	for (int i = 1; i < v.size(); ++i) {
		if (v[i] == temp) //如果当前遍历值与可能过半的数temp相等，则计数加一
			count++;
		else //否则，则计数减一
			count--;
        
		if (count == 0) { //如若计数变为0，则将当前遍历值设为可能过半的数temp，并将其计数置为1
			temp = v[i];
			count++;
		}
	}

	cout << temp << endl;

	return 0;
}
```
