题目：
==
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

Example 1: Input:nums = [1,1,1], k = 2 Output: 2

分析：
==
（真切的感受到，让我不能为力的不是如何写代码，而是说很多题我理解不了题意，这道题还好我能理解，不然就要崩溃了）这道题给了我们一个数组，让我们求和为k的连续子数组的个数，简单粗暴往往最能解决问题，上代码

代码:
==
```C
int subarraySum(int* nums, int numsSize, int k) {
    int result=0,l=numsSize;
        for (int i=0;i<l;i++) {
            int sum=nums[i];
            if(sum==k) ++result;
            for(int j=i+1;j<l;j++) {
                sum=sum+nums[j];
                if (sum==k) ++result;
            }
        }
        return result;
}
```

总结感受：
==
一开始想的直接是nums[i]+nums[j],没有赋给sum以nums[i]的值，然后就wrong answer，改掉了这里，还是不对，仔细检查，发现有可能单个元素的子数组就等于k啊，又加了if语句来判断，终于ac了。

