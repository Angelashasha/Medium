题目：
==
Given two integers n and k, you need to construct a list which contains n different positive integers ranging from 1 to n and obeys the following requirement: 
Suppose this list is [a1, a2, a3, ... , an], then the list [|a1 - a2|, |a2 - a3|, |a3 - a4|, ... , |an-1 - an|] has exactly k distinct integers.

If there are multiple answers, print any of them.
```
Example 1:
Input: n = 3, k = 1
Output: [1, 2, 3]
Explanation: The [1, 2, 3] has three different positive integers ranging from 1 to 3, and the [1, 1] has exactly 1 distinct integer: 1.
Example 2:
Input: n = 3, k = 2
Output: [1, 3, 2]
Explanation: The [1, 3, 2] has three different positive integers ranging from 1 to 3, and the [2, 1] has exactly 2 distinct integers: 1and2.
```
分析：
==
给出两个整数，n和k，要求在从1到k的范围内找到一定的数构成数组，使相邻元素的差的绝对值构成的数组大小为k。元素差最多的个数是n-1个，这n-1个数的较大的数和较小的数交替形成的序列就满足要求。若k不等于n-1，我们只需要按规律形成满足k-1的序列，剩余序列按递减序即可（剩余的差值都为1）。

代码：
==
```C++
class Solution {
public:
    vector<int> constructArray(int n, int k) {
        vector<int>ret;
        for(int i=1,j=n;i<=j;)
        {
            if(k>1){
                if(k%2==0)
                 ret.push_back(i++);
                else
                    ret.push_back(j--);
                k--;
                }
            else{
                 if(k%2==0)
                 ret.push_back(i++);
                else
                    ret.push_back(j--);
            }
        }
        return ret;
    }
};
```
总结与反思：
==
只想说自己是有多傻敷敷，for里面最后没有加;所以一直Memory Time Exceed Error，绝望！
