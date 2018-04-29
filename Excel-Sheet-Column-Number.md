题目：
==
Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
```
Example 1:
Input: "A"
Output: 1
```
```
Example 2:
Input: "AB"
Output: 28
```
```
Example 3:
Input: "ZY"
Output: 701
```
分析：
==
题目要求我们将英文字母转化为数字返回，A-Z分别是1-26，然后第二位按照A-Z的顺序继续排，给定任意一个字符串，让我们求其得到的数字。我一开始把题目想复杂了，我想过一个一个先把字母对应到相应的数字，然后再所有的数字逐次加起来，但我就觉得这样不就太麻烦了，看之前的人做过的是直接26进制转化为10进制，也就是说逐个读入字符串中的每一个字符进行处理转换即可。但是要注意因为A是从1开始而不是从0所以要加一。

代码：
==
```C++
class Solution {
public:
    int titleToNumber(string s) {
        int ret= 0;  
        int tmp= 0;  
        for (int i=0;i<s.size();i++) 
        {  
            tmp= s[i]-'A'+1;  
            ret= 26*ret+tmp;  
        }  
        return ret;  
    }
};
```
