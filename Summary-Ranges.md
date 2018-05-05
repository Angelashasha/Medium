题目：
==
Given a sorted integer array without duplicates, return the summary of its ranges.

Example 1:
Input: [0,1,2,4,5,7]
Output: ["0->2","4->5","7"]

Example 2:
Input: [0,2,3,4,6,8,9]
Output: ["0","2->4","6","8->9"]

分析：
==
题目给定一组无重复数字的排序后的数，让我们找出连续序列，并用->连接，不连续的直接返回该数即可。其实这个问题也不难，于是我就头脑简单的写了如下代码：
```C++
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> ret;
        for(int i=0;i<nums.size()-1;i++)
        {
            if(nums[i+1]=nums[i]+1)
            {
                ret.push_back(to_string (nums[i]));
                ret.push_back("->");
                ret.push_back(to_string (nums[i+1]));
            }
            else
                ret.push_back(to_string (nums[i]));
        }
        return ret;
    }
};
```
当我运行之后，我发现自己好像个小傻瓜，不但元素重复出现没有考虑，甚至连输出格式都不合适，一开始写的时候我还想着连续序列要以一个字符串的形式呈现，不知道怎么写着写着就忘了。没事，我改
 
代码：
==
```C++
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> ret;
        int i=0,l=nums.size();
        while (i<l) 
        {
            int j=1;
            while(i+j<l &&nums[i+j]-nums[i]==j) j++;
            ret.push_back(j<=1? to_string(nums[i]):to_string(nums[i])+"->" +to_string(nums[i+j-1]));
            i+=j;
        }
        return ret;
    }
};
```
定义两个变量i和j，i用来记录连续序列起始数字的位置，j记录连续数列的长度，j为1说明其后不连续，若不为1则是连续序列，再按照要求返回即可。
