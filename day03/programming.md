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
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; <br>

- **【代码】**<br>
```c++

```
