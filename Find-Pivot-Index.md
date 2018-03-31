题目：
==
Given an array of integers nums, write a method that returns the "pivot" index of this array.

We define the pivot index as the index where the sum of the numbers to the left of the index is equal to the sum of the numbers to the right of the index.

If no such index exists, we should return -1. If there are multiple pivot indexes, you should return the left-most pivot index.
```
Example 1:
Input: 
nums = [1, 7, 3, 6, 5, 6]
Output: 3
Explanation: 
The sum of the numbers to the left of index 3 (nums[3] = 6) is equal to the sum of numbers to the right of index 3.
Also, 3 is the first index where this occurs.
Example 2:
Input: 
nums = [1, 2, 3]
Output: -1
Explanation: 
There is no index that satisfies the conditions in the problem statement.
```
分析：
==
题目要求我们在数组中找到一个数，其前面数字的和等于后面的数字之和。定义一个数组，使其每个元素为给定的数组当前位置之前的数字之和。然后再次遍历这个数组，如果这个元素等于最后一个元素即所有元素之和减去当前位置之后的原数组的数字之和，就返回下标值即可。

代码：
==
```C++
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
           int l=nums.size();
        vector<int> sums(l+1,0);
        for (int i=1;i<sums.size();i++) {
            sums[i]=sums[i-1] +nums[i-1];
        }
        for (int i=0;i<sums.size()-1;i++) {
            if (sums[i]==sums[l]-sums[i+1]) {
                return i;
            }
        }
        return -1;
    }
};
```
