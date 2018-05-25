题目：
==
Given a string S and a character C, return an array of integers representing the shortest distance from the character C in the string.
```
Example 1:
Input: S = "loveleetcode", C = 'e'
Output: [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]
```
分析：
==
题目给出一个字符串和一个字母，让我们返回每个字母与给定字母的最小距离。建立一个数组保存C出现的所有位置，遍历S字符串，将其与C中保存的位置依次求距离(比较差的绝对值即可)，然后保存下来最短距离就可以。

代码：
==
```C++
class Solution {
public:
    vector<int> shortestToChar(string S, char C) {
        vector<int> ret(S.size(),0);
        vector<int> position;
        for(int i=0;i<S.size();i++)
            if(S[i]==C)
                position.push_back(i);
        for(int i=0;i<S.size();i++)
        {
             if(S[i]!=C)
             {
                int tmp= S.size();
                for(int j = 0;j<position.size();j++)
                    tmp=tmp<abs(position[j]-i)?tmp:abs(position[j]-i);
                ret[i]=tmp;
             }
        }
        return ret;
    }
};
```
