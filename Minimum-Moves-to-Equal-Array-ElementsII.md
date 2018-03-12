题目：
==
Given a non-empty integer array, find the minimum number of moves required to make all array elements equal, where a move is incrementing a selected element by 1 or decrementing a selected element by 1.

You may assume the array's length is at most 10,000.

Example:

Input:
[1,2,3]

Output:
2

Explanation:
Only two moves are needed (remember each move increments or decrements one element):

[1,2,3]  =>  [2,2,3]  =>  [2,2,2]

分析：
==
这道题和上一道差不多，但是这道题是每次任意一个数可以加或者减，那么最终应当是都成为中间值。通过一些简单的排序后的数尝试，我发现如果数组有奇数个，那么最后就成了最中间的那个值，如果有偶数个，就是最中间那两个中的一个，步数是一样的。所以只要找出所有数与中间值的差求和即可。一开始的时候我是想要分奇偶来写的，想了想没有必要，反正偶数时中间两个数之一即可，那我不如就按照奇数时的算法，直接找l/2处的元素就好啦

代码：
==
```C++
class Solution {
public:
    int minMoves2(vector<int>& nums) {
        int l=nums.size();
        sort(nums.begin(),nums.end());
        int sum=0;
        for(int i=0;i<l;i++){
          sum=sum+abs(nums[i]-nums[l/2]);
      }
        return sum;
    }
};
```

总结体会：
==
我的思路从一开始就是很清晰的，但是在编程实现的时候，一开始没有考虑到绝对值，运行时报错，才想到自己的错误，本想对下标判断与中间位置的大小关系来着，百度了一下，突然发现了绝对值，可以说是很开心了。
