题目：
==
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k. 

分析：
==
给出一个数组和一个整数，在数组中找出两个相同元素并且两元素下标之差的绝对值最大不超过给出的k就返回true。只需遍历找到两个相同元素并判断他们下标之差符不符合要求即可。

代码：
==
```C
bool containsNearbyDuplicate(int* nums, int numsSize, int k) {
    for(int i=0;i<numsSize;i++){
        for(int j=i+1;j<numsSize;j++){
            if(nums[i]==nums[j]&&(abs(i-j)<=k))
                return true;
        }
    }
    return false;
}
```

总结体会：
==
需要注意的一点是下标之差的绝对值不超过k，其实是可以等于k的，我一开始理解成了必须小于k。
