题目:
==
Your are given an array of positive integers nums.

Count and print the number of (contiguous) subarrays where the product of all the elements in the subarray is less than k.

```
Example 1:
Input: nums = [10, 5, 2, 6], k = 100
Output: 8
Explanation: The 8 subarrays that have product less than 100 are: [10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6].
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
```
分析：
==
题目给出一个正数数组，要求找出乘积小于给定的整数K的连续数组的个数。用current记录到当下元素为止所有的乘积，如果乘积大于给定的整数，就记录到他前一个数，用res记录符合要求的数组的个数。

代码：
==
```C++
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {
         if (k<=1) return 0;
        int res=0,current=1,left=0;
        for (int i=0; i<nums.size();i++) {
            current*= nums[i];
            while (current>=k) 
            {current/=nums[left];
               left++;
            }
             res+=i-left+1;
        }
        return res;
    }
};
```
