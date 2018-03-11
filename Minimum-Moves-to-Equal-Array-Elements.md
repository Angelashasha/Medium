题目：
==
Given a non-empty integer array of size n, find the minimum number of moves required to make all array elements equal, where a move is incrementing n - 1 elements by 1.

Example:

Input:
[1,2,3]

Output:
3

Explanation:
Only three moves are needed (remember each move increments two elements):

[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]

分析：
==
题目给定一个长度为n的非空整数数组，要求我们每次同时移动数组中的n-1个数，使他们都增加1。求解需要最少移动多少步，可以使数组中各数字最后相等。
每次操作都是要把最小的n-1个元素都加1，那其他元素的增就相当于最大元素的减，题目要求最后的元素值相同即可，那我们可以认为是所有元素最终都等于元素最小值，那么最小的步数也就是每个元素与最小元素的差的和。

代码：
==
```C++
class Solution {
public:
    int minMoves(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int l=nums.size();
        int sum=0;
        for(int i=0;i<l;i++)
           sum=sum+nums[i]-nums[0];
        return sum;        
    }
};
```

总结体会：
==
真的按一步一步加去想，我的脑子一片凌乱。参考一下网上的，一开始看到这样的思路的时候其实我是拒绝的，看了几个，发现都是这种思路，我就仔细想了一下，一开始觉得很别扭，理解不了，后来一下子就豁然开朗了，最终的目的很明确，直接的路径我们想不出，可以等效啊，一下子就变得简单了。
