题目:
==
You are given a string representing an attendance record for a student. The record only contains the following three characters:
'A' : Absent.
'L' : Late.
'P' : Present.
A student could be rewarded if his attendance record doesn't contain more than one 'A' (absent) or more than two continuous 'L' (late).

You need to return whether the student could be rewarded according to his attendance record.
```
Example 1:
Input: "PPALLP"
Output: True

Example 2:
Input: "PPALLL"
Output: False
```
分析：
==
题目给出三个字符分别代表不同的出勤状态，如果有一次以上缺勤或者连续迟到两次以上就不能评奖，要求写一个程序来判断某学生是否可以得奖。遍历即可，设定一个计数器来记录出现的A的次数，每次出现A判断计数器是否大于1，判断是否有连续三天迟到的情形，若符合这两者之一，即判断为不可得奖。其余情况即为可得奖。

代码：
==
```C++
class Solution {
public:
    bool checkRecord(string s) {
         int cntA=0;
         int i=0;
        while(s[i]!='\0')
        {
            if(s[i]=='A') 
            {
                  cntA++;
                if(cntA>1)
                    return false;
            }
            if(s[i]=='L'&&s[i+1]=='L'&&s[i-1]=='L')
               return false;
            i++;
        }
        return true;
    }
};
```

总结思考：
==
虽然题目很简单，但是并不是一遍过，遗憾，出现了两个错误，一是没有理解出现多于连续两天的迟到，认为是连续迟到两天，再者是在出现A的时候，先判断了计数器的值是否大于1，这样到出现第三个A时计数器才为2导致出错。
