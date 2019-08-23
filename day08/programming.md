### 1. 标题：[两种排序方法](https://www.nowcoder.com/practice/839f681bf36c486fbcc5fcb977ffe432?tpId=85&&tqId=29844&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>
&#160; &#160; &#160; &#160; 本题我们可将接收到的所有字符串都保存在一个vector中，接着遍历这个vector，利用string的operator<运算符重载按ASCII比较字符串，利用string的length来比较字符串的长度即可。<br>

- **【代码】**
```c ++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main() {
    vector<string> v;
    int n = 0;
    
    cin >> n;
    v.resize(n);
    
    for(size_t i=0; i<n; ++i) {
        cin >> v[i];
    }
    
    bool dictionary = true, length = true;
    for(size_t i=1; i<n; ++i) {
        if(v[i] < v[i-1]) //判断是否根据字典序排列
            dictionary = false;
        if(v[i].length() < v[i-1].length()) //判断是否根据长度排列
            length = false;
        if(dictionary == false && length == false) {
            cout << "none" << endl;
            return 0;
        }
    }
    
    if(dictionary == true && length == false)
        cout << "lexicographically" << endl;
    else if(dictionary == false && length == true)
        cout << "lengths" << endl;
    else if(dictionary == true && length == true)
        cout << "both" << endl;
    
    return 0;
}
```

### 2. 标题：[求最小公倍数](https://www.nowcoder.com/practice/22948c2cad484e0291350abad86136c3?tpId=37&&tqId=21331&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>
&#160; &#160; &#160; &#160; 由于两个数的最小公倍数等于两数之积除以最大公约数，所以我们可以利用辗转相除法先求出两个数的最大公约数，再进一步求出最小公倍数。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int gcd(int a, int b) { //辗转相除法求两数最大公约数
    while(a%b) {
        int tmp = a;
        a = b;
        b = tmp % b;
    }
    return b;
}

int main() {
    int a = 0, b = 0;
    
    while(cin >> a >> b) {
        cout << a*b/gcd(a,b) << endl; //最小公倍数 = 两数之积/最大公约数
    }
    
    return 0;
}
```
