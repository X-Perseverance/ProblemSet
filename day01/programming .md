### 1. 标题：[组队竞赛](https://www.nowcoder.com/questionTerminal/6736cc3ffd1444a4a0057dee89be789b?orderByHotValue=1&page=1&onlyReference=false)

- **题目解析：**<br>

&#160; &#160; &#160; &#160; 每一个队伍的水平值等于该队伍队员中第二高水平值，为了使所有队伍的水平值总和最大，也就要求每个队伍的第二个值是尽可能大的值。所以实际值要把最大值放到最右边，最小值放到最左边。<br>

- **解题思路：**<br>

&#160; &#160; &#160; &#160; 本题的主要思路是贪心算法，贪心算法其实很简单，就是每次选值时都选当前能看到的局部最优解，所以这里的贪心就是保证每组的第二个值取到能选择的最大值就可以，我们每次尽量取最大，但是最大的数不可能是中位数，所以退而求其次，取每组中第二大的。<br>
&#160; &#160; &#160; &#160; 排序，然后取下标为 3n - 2，3n - 4 ，3n - 4... n+2，n 位置的元素累加即可，相当下标为[0,n-1]的n个数做每组的最左边的数，剩下的2个数据两个为一组，大的值做最右边的数，次大的做中间值，这里就是把这个次大的值加起来。<br>
&#160; &#160; &#160; &#160; 例如：现在排序后有 1 2 5 5 8 9 ，那么取 8 和 5 相加等于 13。<br>

- **代码：**<br>
```c++
#include <iostream>
#include <vector>
#include <algorithm>
 
using namespace std;
 
int main() {
    int n = 0;
     
    while(cin >> n) {
        vector<int> v;
        v.resize(3*n);
         
        for(int i=0; i<3*n; ++i)
            cin >> v[i];
         
        sort(v.begin(), v.end());
         
        long long maxSum = 0;
        for(int i=n; i<=3*n-2; i=i+2)
            maxSum += v[i];
         
        cout << maxSum << endl;
    }
     
    return 0;
}
```

### 2. 标题：[删除公共字符](https://www.nowcoder.com/practice/f0db4c36573d459cae44ac90b90c6212?tpId=85&&tqId=29868&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)

- **解题思路：**<br>

- [ ] 传统方法：<br>

> &#160; &#160; &#160; &#160; （1）判断第一个字符串中的每一个字符是否在第二个字符串中；<br>
> &#160; &#160; &#160; &#160; （2）若存在，则挪动后面的字符依次覆盖前一个字符；若不存在，则判断下一个字符。<br>
> &#160; &#160; &#160; &#160; 这种方法的时间复杂度为 `O(N^2)`，效率太低，很难让人满意。<br>

- [x] 高级方法：<br>

> &#160; &#160; &#160; &#160; （1）将第二个字符串中的字符都映射到一个 hashtable数组 中，以便用来判断第一个字符串中的字符是否在第二个字符串中；<br>
> &#160; &#160; &#160; &#160; （2）定义一个新字符串，作为最后的结果；<br>
> &#160; &#160; &#160; &#160; （3）依次遍历第一个字符串的字符，若其不在第二个字符串，则将该字符添加到上述新字符串中；若存在，则遍历下一个。<br>
> &#160; &#160; &#160; &#160; 这种方法的时间复杂度为 `O(N)`，相对于上一种方法，其效率大幅提升。因为在这里，我们并不需要完整地去遍历第二个字符串才能判断出一个字符是否存在，而是直接去hashtable数组中查找一次即可。此外，在这种方法中并没有进行数据的挪动，而是将不存在的字符组合成一个新字符串作为结果输出。<br>

- **代码：**<br>
```c++
#include <iostream>
#include <string>
 
using namespace std;
 
int main() {
    string str1, str2;
    getline(cin, str1);
    getline(cin, str2);
     
    int hashTable[256]={0};
    for(size_t i=0; i<str2.size(); ++i)
        hashTable[str2[i]]++;
     
    string ret;
    for(size_t i=0; i<str1.size(); ++i) {
        if(hashTable[str1[i]] == 0)
            ret += str1[i];
    }
     
    cout << ret << endl;
     
    return 0;
}
```
