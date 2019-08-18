### 1. 标题：[两种排序方法](https://www.nowcoder.com/practice/839f681bf36c486fbcc5fcb977ffe432?tpId=85&&tqId=29844&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

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
        if(v[i] < v[i-1])
            dictionary = false;
        if(v[i].length() < v[i-1].length())
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
    else
        cout << "none" << endl;
     
    return 0;
}
```

### 2. 标题：[求最小公倍数](https://www.nowcoder.com/practice/22948c2cad484e0291350abad86136c3?tpId=37&&tqId=21331&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

- **【代码】**
```c ++
#include <iostream>
 
using namespace std;
 
int main() {
    int A=0, B=0;
     
    while(cin >> A >> B) {
        size_t i = min(A, B);
        for( ; i>1; --i) {
            if(A%i==0 && B%i==0)
                break;
        }
        cout << (A/i)*B << endl;
    }
     
    return 0;
}
```
