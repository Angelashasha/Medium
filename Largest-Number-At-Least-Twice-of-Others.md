题目：
==
In a given integer array nums, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the index of the largest element, otherwise return -1.
```
Example 1:

Input: nums = [3, 6, 1, 0]
Output: 1
Explanation: 6 is the largest integer, and for every other number in the array x,
6 is more than twice as big as x.  The index of value 6 is 1, so we return 1.
```
```
Example 2:

Input: nums = [1, 2, 3, 4]
Output: -1
Explanation: 4 isn't at least as big as twice the value of 3, so we return -1.
```
分析：
==
题目要求我们在数组中找到这样的一个数，这个数至少要大于其余各数的2倍，如果有这样的一个数，就返回这个数的下标，若没有，就返回-1。我的想法就是我先找到涉足力量的最大数，记录他的数值和下标，然后再遍历看是否符合大于其余各数的两倍这个要求。

代码：
==
```C
int dominantIndex(int* nums, int numsSize) {
    int max=0,index;
for(int i=0;i<numsSize;i++)
{
    if(nums[i]>max)
    {max=nums[i];
     index=i;}
}
    for(int i=0;i<numsSize;i++)
{        if(i!=index){
    {   if(max<2*nums[i])
        return -1;
    }
        }
}
    return index;
}
```
总结体会:
==
题目很简单了，但是wrong了一次，因为在第二次遍历的时候没有考虑到去掉和本身的二倍相比较。
