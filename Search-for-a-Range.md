题目：
==
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

例如，给定[5, 7, 7, 8, 8, 10]，目标值为8，返回[3, 4]。

分析：
==
给定一个整型已排序数组，找到一个给定值在其中的起点与终点。如果目标在数组中不会被发现，返回[-1, -1]。类似于二分查找，但是当等于目标值时需要向左向右对其相邻元素进行判断。

代码：
==
```C++
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
     int left=0;  
     int right=nums.size()-1;  
          vector<int> result;  
        result.push_back(-1);  
        result.push_back(-1);  
          while(left<=right)  
        {  
            int mid=(left+right)/2;  
            if(nums[mid]>target)  
            {  
                right=mid-1;  
            }  
            else if(nums[mid]<target)  
            {  
                left=mid+1;  
            }  
            else  
            {  
                result[0]=mid;  
                result[1]=mid;  
                int j=mid-1;  
                while(j>=0&&nums[j]==target)  
                {  
                    result[0]=j;  
                    j--;  
                }  
  
                j=mid + 1;  
                while(j<nums.size()&&nums[j]==target)  
                {  
                    result[1]=j;  
                    j++;  
                }  
                break;  
            }  
        }  
       return result;  
    }
};
```
