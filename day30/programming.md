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

　　

- **【代码】**
```c ++

```
