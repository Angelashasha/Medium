题目：
==
Given a collection of distinct integers, return all possible permutations.
```
Example:
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```
分析：
==
题意简洁明了，找到一个数组所有的排列方式。放在数学里，就是一个敲简单的排列组合问题，选一个元素做第一个数，在剩下的里面再选一个做第二个数，一直到所有数都被选完，很明显这里要用到递归，在递归过程中，要完成的操作是，用tmp来储存已经选好的数，被选过就要将他在原数组nums中删除，以保证不会被重复选择，这样子nums中储存的就是待选数字，而每一次permuteFind函数返回后，nums就要插入元素成为原来的样子，tmp删除元素，进行另一种方式的排列。当nums中为空时就说明结束了，将tmp中储存的数都储存到ret中，返回ret数组即可。

代码：
==
```C++
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<int> tmp;
        vector<vector<int> > ret;
        permuteFind(ret,tmp,nums);
        return ret;
    }
    void permuteFind(vector<vector<int> > &ret,vector<int> &tmp,vector<int> &nums)
    {
        if(nums.empty())
        {
            ret.push_back(tmp);
        }
        for(int i=0;i<nums.size();i++)
        {  int n=nums[i];
           tmp.push_back(n);
           nums.erase(nums.begin()+i);
           permuteFind(ret,tmp,nums);
           nums.insert(nums.begin()+i,n);
           tmp.pop_back();
        }
    }
};
```
