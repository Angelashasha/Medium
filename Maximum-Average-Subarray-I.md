题目：
==
Given an array consisting of n integers, find the contiguous subarray of given length k that has the maximum average value. And you need to output the maximum average value.

Example 1:
Input: [1,12,-5,-6,50,3], k = 4
Output: 12.75
Explanation: Maximum average is (12-5-6+50)/4 = 51/4 = 12.75

分析：
==
题目要求找到连续的平均值最大的k个数，我的想法是先算出前k个数字的和，然后加上下一个元素，即加上一个右边的数字，再减去一个左边的数字，每次res取sum与res的最大值，最后返回res/k的结果即可。

代码：
==
```C++
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
         double sum=0.0;
        for(int i=0;i<k;i++)
            sum+=nums[i];
        double res=sum;
        for (int i = k; i < nums.size(); ++i) {
            sum+=nums[i]-nums[i - k];
            res=max(res, sum);
        }
        return res/k;
    }
};
```
