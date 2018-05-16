题目:
==
Given string S and a dictionary of words words, find the number of words[i] that is a subsequence of S.
```
Example :
Input: 
S = "abcde"
words = ["a", "bb", "acd", "ace"]
Output: 3
Explanation: There are three words in words that are a subsequence of S: "a", "acd", "ace".
```
分析：
==
给出一个字符串，要求我们找出在一个给定的字符串数组中有多少个字符串与给出的字符串相匹配。暴力解决的话就是一个个匹配试一下咯，但是超时，我上网参考了一下别人的做法。整体思路就是通过队列，依据字符的不同，记录下一个字符所有的数组下标。利用下标递增的思想，方便利用二分法查找。

代码：
==
```C++
class Solution {
public:
    int numMatchingSubseq(string S, vector<string>& words) {
         map<int,vector<int> > m;  
        for(int i=0;i<S.length();i++)  
            m[S[i]-'a'].push_back(i);  
        int cnt = 0;  
        for(auto word:words){  
            int cur=- 1;  
            for(int i=0;i<word.length();i++){  
                auto temp=upper_bound(m[word[i]-'a'].begin(),m[word[i]-'a'].end(),cur);  
                if(temp==m[word[i]-'a'].end()) break;  
                   cur=*temp;  
                if(i==word.length()-1) cnt++;  
            }  
        }  
        return cnt;  
    }
};
```
