,题目：
==
Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.
Find all the elements that appear twice in this array.
Could you do it without extra space and in O(n) runtime?

Example:
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]

分析：
==
题目要求我们在给出的一组数中找出出现了两次的数并返回。找重复的话，做标记是个好办法，不额外申请空间的话，就得改变原本数组元素的值,所以把数组中的i出现对nums[i-1]这个元素进行标记，最简单的方式就是取反，所以每当元素i出现一次，nums[i-1]=-nums[i]最后返回的就是出现两次的

代码：
==
```C++
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
          vector<int> ret;
        for (int i=0;i<nums.size();i++) {
            nums[abs(nums[i])-1]=-nums[abs(nums[i])-1];
            if(nums[abs(nums[i])-1]>0)
                ret.push_back(abs(nums[i]));
        }
        return ret;
    }
};
```
