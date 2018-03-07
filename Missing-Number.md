题目：
==
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

Example 1

Input: [3,0,1]
Output: 2
Example 2

Input: [9,6,4,2,3,5,7,0,1]
Output: 8

分析：
==
题目给出一个n个元素的数组，数组元素是从0到n中选出来的，让我们找到数组中没有的那个数字，最简单粗暴的想法，排序，遍历，如果数字全的话，那每个元素的下标都应该与该数字相等，如果不相等，那么这个下标就是丢失的数字。

代码：
==
```C++
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int l=nums.size();
        int i;
        for(i=0;i<l;i++)
            if(nums[i]!=i){
                break;
            }
         return i;
    }
};
```

另外一种做法：
```C++
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int result=0;
        int l=nums.size();
        for (int i=0;i<l;i++) {
            result=result^(i+1)^ nums[i];
        }
        return result;
    }
};
```
这种做法利用的是异或操作，既然所有数都是从0到n中选的，那么我们就把完整数组与给的数组进行异或操作，相同的都变成了0，最后剩下的就是没有出现在数组中的。
