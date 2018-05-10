题目：
==
Given a set of distinct integers, nums, return all possible subsets (the power set).
```
Example:
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```
分析：
==
题目要求找出所有的子集，对于数组[1,2,3]，可以用一个下标0和1表示是否选择了该数字，0表示未选择，1表示选中，那么每一组3个0和1的组合表示一种选择，为1的位表示数组中该位被选中。那么只需要遍历0到1<< length中的数，判断每一个数中有那几位为1，将是1的那几位加入数组构成一个子集中的一个元素。

代码：
==
```C++
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
         int l=nums.size();
        sort(nums.begin(),nums.end());
        vector<vector<int> > ret;
        for(int i=0;i<1<<l;i++)
        {
            vector<int> tmp;
            for(int j=0;j<l;j++)
            {
                if(i&1<<j)
                {
                    tmp.push_back(nums[j]);
                }
            }
            ret.push_back(tmp);
        }
        return ret;
    }
};
```
