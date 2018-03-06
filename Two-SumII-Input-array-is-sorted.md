题目：
==
Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2

分析：
==
给定已排序的数组，让我们找到相加等于目标数字的两个数，并按从大到小的顺序返回基于1的情况下这两个数的下标。既然是排序好的，那就从最大加最小开始试，小了就往后找一个数，大了就往前找一个数，这样子左边的数的下标永远小于右边的大数的下标，方便记录到数组中。

代码：
==
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int left=0;
        int right=numbers.size()-1;
        vector<int> result(2,0);
        while(left<right)
        {
            int temp=numbers[left]+numbers[right];
            if(temp==target)
            {
                result[0]=left+1;
                result[1]=right+1;
                return result;
            }
            else if(temp<target)
                left++;
            else
                right --;
    }
    }
};
```

不考虑排序的方法：
==
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int l=numbers.size();
        vector<int> result(2,0);
      for(int i=0;i<l;i++){
          for(int j=i+1;j<l;j++){
              if(numbers[i]+numbers[j]==target)
              {
                  result[0]=i<j?i:j;
                  result[1]=i>j?i:j;
              }
          }
      }
        result[0]=result[0]+1;
        result[1]=result[1]+1;
        return result;
    }
};
```
