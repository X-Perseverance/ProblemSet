### 1. 标题：[最难的问题](https://www.nowcoder.com/questionTerminal/9f6b8f6ec26d44cfb8fc8c664b0edb6b)
- **【解题思路】**

　　本题题意明确，容易理解，主要分为两种情况讨论：<br>
　　（1）当密码字母位于 `F ~ Z` 时，原文字母 = **密码字母 - 5**；<br>
　　（2）当密码字母位于 `A ~ E` 时，原文字母 = **密码字母 + 21**。<br>

- **【代码】**
```c
#include <stdio.h>

int main() {
	char c;

	while ((c = getchar()) != EOF) {
		if (c >= 'A' && c <= 'Z') {
			c = (c > 'E') ? (c - 5) : (c + 21);
		}
		putchar(c);
	}

	return 0;
}
```

### 2. 标题：[因子个数](https://www.nowcoder.com/questionTerminal/e8fb8f89f5d147ec92fd8ecfefe89b0d)
- **【解题思路】**

　　本题所要求解的是每一个正整数的因子个数，而这里的**因子**其实指的就是[质因子](https://baike.baidu.com/item/%E8%B4%A8%E5%9B%A0%E5%AD%90)，为了求出因子的个数，我们首先需要理解一下[分解质因数](https://baike.baidu.com/item/%E5%88%86%E8%A7%A3%E8%B4%A8%E5%9B%A0%E6%95%B0)的过程。<br>
　　在分解质因数的时候，要从最小的质数除起，一直除到结果为质数为止，具体的过程见代码。<br>

- **【代码】**
```C++
#include <iostream>
#include <cmath>

using namespace std;

int main() {
    int n = 0;
    
    while(cin >> n) {
        int count = 0; //因子个数
        
        for(int i=2; i<=sqrt(n); ++i) { //从最小的质数开始，对n进行整除
            if((n%i) == 0) { //若n能整除以当前质数，则说明当前质数就是一个质因子
                while((n%i) == 0) { //让当前质数不断整除n，直到当前质数无法整除n为止
                    n /= i;
                }
                count++; //将当前质数统计到因子个数中，然后使用下一个质数进行计算
            }
        }
        if(n != 1) //若除到最后，n也是一个质数，则因子个数加一
            count++;
        
        cout << count << endl;
    }
    
    return 0;
}
```
