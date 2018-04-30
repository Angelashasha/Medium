
题目：
==
Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...
```
Example 1:
Input: 1
Output: "A"
```
```
Example 2:
Input: 28
Output: "AB"
```
```
Example 3:
Input: 701
Output: "ZY"
```
分析：
==
这道题和昨天那个差不多，所以这个就是10进制转化为26进制即可。

代码：
==
class Solution {
public:
    string convertToTitle(int n) {
        string ret="";//好几次都不A，结果一样，但我没有注意到空格，发现是初始化他为空格
        while(n)
        {
            ret=(char)((n-1)%26+'A')+ret;
            n=(n-1)/26;
        }
        return ret;
     }
};
