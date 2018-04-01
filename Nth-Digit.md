题目：
==
Find the nth digit of the infinite integer sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...
```
Example 1:

Input:
3

Output:
3
Example 2:

Input:
11

Output:
0

Explanation:
The 11th digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.
```
分析;
==
把自然数序列看成一个长字符串，求N位上的数字是什么，那么关键就是要找出第N位所在的数字。可以把数字转为字符串，这样就直接可以访问任何一位。首先来分析自然数序列和位数之间的关系，前九个数都是1位，然后10到99总共90个数字都是两位的，100到999这900个数都是三位的，显然是有规律的，我们可以定义一个变量cnt，初始化他为9，然后每次循环扩大10倍，再用一个变量len记录当前循环区间数字的位数，另外再需要一个变量start用来记录当前循环区间的第一个数字，我们n的每次循环都减去len*cnt (区间总位数)，当n落到某一个确定的区间里时，(n-1)/len就是我们要找的数在该区间里的位置，再加上start就得到了所要找的数，然后把他转化为为字符串，(n-1)%len就是所要求的目标位置。

代码：
==
```C++
class Solution {
public:
    int findNthDigit(int n) {
        long long len=1,cnt=9,start=1;//避免int型溢出，直接定义为长整型
        while (n>len*cnt) {
            n-=len*cnt;
            len++;
            cnt*=10;
            start*=10;
        }
        start+=(n-1)/len;
        string ret=to_string(start);
        return ret[(n-1)%len]-'0';
    }
};
```
