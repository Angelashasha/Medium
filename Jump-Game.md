题目：
==
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

```
Example 1:

Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```
```
Example 2:

Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
```
分析：
==
根据题目要求，数组里的每个元素表示从该位置可以跳出的最远距离，要求问从第一个元素即index=0开始，能否达到数组的最后一个元素，这里说的是到达，就说明超过也行，
用一个变量terminal，来记录能跳到的最后的位置。对第i步来说，从第i个位置出发的最远是nums[i]+inums[i]+i那么terminal=max(terminal,nums[i]+i),一旦i比terminal大，就说明跳不到那个位置了，那就更跳不到最后一个了。

代码：
==
```C++
class Solution {
public:
    bool canJump(vector<int>& nums) {
         int i=0,terminal=nums[0];
        for(i=0;i<=terminal&&i<nums.size();i++)
        {
            terminal=max(terminal,nums[i]+i);
        }
        if(i==nums.size())
            return true;
        return false;
  }
};
```
