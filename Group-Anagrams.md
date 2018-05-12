题目：
==
Given an array of strings, group anagrams together.
```
Example:
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```
分析：
==
题目给出字符串数组，让我们找到由出现次数相同的一些字符组成的字符串。这些字符按照字母顺序重新排列的话就是相同的。所以就将所有字符串全部重新排列得到的字符串作为key，将所有能得到这个字符串的都保存在key对应位置的字符串数组中，然后将最终结果存到ret数组中返回即可。

代码：
==
```C++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
         if (strs.empty())
            return vector<vector<string> >();
        int l= strs.size();
        sort(strs.begin(), strs.end());
        vector<vector<string> > ret;
        map<string, vector<string>> tmp;
        for (int i=0;i<l;i++)
        {
            string str=strs[i];
            sort(str.begin(), str.end());

            tmp[str].push_back(strs[i]);
        }
        for (map<string, vector<string> >::iterator i=tmp.begin();i!=tmp.end();i++)
            ret.push_back(i->second);
        return ret;
    }
};
```

