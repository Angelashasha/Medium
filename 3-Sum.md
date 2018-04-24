题目：
==
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.
```
Example:
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```
分析：
==
题目要求我们找到给定的一组数中可以相加得0的三个数，存放在数组中。和2Sum思路差不多，对原数组进行排序，然后开始遍历排序后的数组，遍历到倒数第三个即可，在这个过程中，要注意有重复的数就跳过，而对于遍历到的数，我们用0减去这个数得到一个sum，接下来只要找到两个数之和等于sum即可，这样就又把问题转化为了求2sum，然后扫描，找到等于sum的两数后，加上当前遍历到的数字，按顺序存入结果中即可，这个过程依然要注意跳过重复数字，最终返回数组即可。

代码：
==
```C++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
         vector<vector<int>> res;
        sort(nums.begin(),nums.end());
        for(int k=0;k<nums.size();k++) 
        {
            if(nums[k]>0) break;
            if (k>0&&nums[k]==nums[k-1]) continue;
            int target=0-nums[k];
            int i=k+1,j=nums.size()-1;
            while (i<j) {
                if (nums[i]+nums[j]==target) {
                    res.push_back({nums[k], nums[i], nums[j]});
                    while (i<j&&nums[i]==nums[i + 1]) i++;
                    while (i<j&&nums[j]==nums[j-1])   j--;
                    i++;
                    j--;
                } 
                else if (nums[i]+nums[j]<target) i++;
                else j--;
            }
        }
        return res;
    }
};
```
