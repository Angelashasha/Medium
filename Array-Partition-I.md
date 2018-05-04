题目：
==
Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible. 
Example 1:
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).

分析：
==
题目要求将给定的数两两分组，求每组数中较小的数的和的最大值。我的思路就是排序，继而两两分，将数组偶数位置的数累加即得结果。我怀疑过这个想法是不是就能得到最大的，于是我就自己试了多组数，发现没有错误，于是就大胆地写了。

代码：
==
```C++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
         sort(nums.begin(),nums.end());
          int sum=0;
          for(int i=0;i<nums.size();i+=2)
              sum+=nums[i];
         return sum;
    }
};
```
