题目：
==
Given an array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

分析：
==
除一个元素出现一次，其余都是三次，找到这个只出现一次的数。先排序，后遍历。特殊一点的就是在头或者在尾，首先判断是否是这两种特殊情况，不是的话，就遍历剩下的，如果某一元素与前后两个元素均不相等，那就是这个元素了。

代码：
==
```C++:
class Solution {
public:
    int singleNumber(vector<int>& nums) {
       sort(nums.begin(),nums.end());
        int l=nums.size();
        if(nums[0]!=nums[1])
            return nums[0];
        if(nums[l-1]!=nums[l-2])
            return nums[l-1];
        for(int i=1;i<l-1;i++)
        {
            if(nums[i]!=nums[i+1]&&nums[i]!=nums[i-1])
                return nums[i];
        }
    }
};
```

总结感受：
==
很简单的一道题，因为低级错误两次都没过，忧桑死，第一次是nums.size()的()忘记写，第二次是发现自己全部是和数组的后一个元素比的，唉，傻子。
