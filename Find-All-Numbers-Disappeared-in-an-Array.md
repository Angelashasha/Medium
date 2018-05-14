题目：
==
Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.
```
Example:
Input:
[4,3,2,7,8,2,3,1]
Output:
[5,6]
```
分析：
==
题目要求找到没有出现的数字。对于每个数字nums[i]，如果其对应的nums[nums[i]-1]是正数，就取反，也就是赋值为其相反数，那么最后我们只要把留下的整数对应的位置加入结果ret中即可

代码：
==
```C++
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
         vector<int> ret;
        for (int i=0;i<nums.size();i++) 
        {
            int tmp=abs(nums[i])-1;
            nums[tmp]=(nums[tmp]>0)?-nums[tmp]:nums[tmp];
        }
        for (int i=0;i<nums.size();i++) 
        {
            if (nums[i] > 0) {
                ret.push_back(i + 1);
            }
        }
        return ret;
    }
};
```
