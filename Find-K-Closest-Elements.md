题目：
==
Given a sorted array, two integers k and x, find the k closest elements to x in the array. The result should also be sorted in ascending order. If there is a tie, the smaller elements are always preferred.

问题分析及解决方案：
==
题目给出一个排序后的数组，让我们在数组中找到离给出的数x最近的k个数，并按照递增的顺序返回。根据例子可以看出x可以不是数组中的数，且数组按照从小到大的顺序排列的，那么最后返回的k个数就是在数组中去掉了n-k个距离x大的数后剩下的数组，那么若是删除离得远的那肯定是从两头开始删，比较首尾两个数与x的距离，删除掉距离大的数，直至数组中只剩k个数。。

代码：
==
```C++
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        vector<int> res=arr;
        while(res.size()>k)
        {
            int left=abs(res[0]-x);
            int right=abs(res.back()-x);
            if(left>right)
                res.erase(res.begin());
            else
                res.pop_back();
        }
        return res;
    }
};
```
