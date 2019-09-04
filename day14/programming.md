### 1. 标题：[计算日期到天数转换](https://www.nowcoder.com/practice/769d45d455fe40b385ba32f97e7bcded?tpId=37&&tqId=21296&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 创建一个二维数组，分别保存平年和闰年每月的天数，接着根据输入的年月日对三个变量进行判断（判断年是否为闰年，判断月是否合法，判断日是否合法），若都合法，那么累加求和即可求出所转换后的天数。<br>

- **【代码】**
```c ++
#include <iostream>

using namespace std;

int main()
{
	int days[2][13] = {
		{0,31,28,31,30,31,30,31,31,30,31,30,31},
		{0,31,29,31,30,31,30,31,31,30,31,30,31} };
	
	int year = 0, month = 0, day = 0;

	while (cin >> year >> month >> day) {
		int flag = 0; //闰年标志
		int sum = 0;
		if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) //year是否为闰年
			flag = 1;
		if (month > 0 && month < 13) { //month是否合法
			if (day > 0 && day <= days[flag][month]) { //day是否合法
				while (--month) //累加天数
					sum += days[flag][month];
				sum += day;
				cout << sum << endl;
			}
			else
				cout << "-1" << endl;
		}
		else
			cout << "-1" << endl;
	}

	return 0;
}
```

### 2. 标题：[幸运的袋子](https://www.nowcoder.com/practice/a5190a7c3ec045ce9273beebdfe029ee?tpId=85&&tqId=29839&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking)
- **【解题思路】**<br>

&#160; &#160; &#160; &#160; 

- **【代码】**
```c ++

```
