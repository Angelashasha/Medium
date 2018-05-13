题目：
==
Given a n x n matrix where each of the rows and columns are sorted in ascending order, find the kth smallest element in the matrix.
```
Example:
matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,
return 13.
```
分析：
==
题目给出一个n阶矩阵，其中矩阵的每行每列都按照从小到大的顺序排列，要求找出第k小的元素。我的做法就比较简单粗暴了，我将矩阵所有的元素都存放到一个数组里，然后将这个数组进行排列，输出其第k-1个元素，即为矩阵第k小的元素。

代码：
==
```C++
class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        vector<int> tmp;
        int l=matrix.size();
        for(int i=0;i<l;i++)
            for(int j=0;j<l;j++)
            {
                tmp.push_back(matrix[i][j]);
            }
        sort(tmp.begin(),tmp.end());
        return tmp[k-1];
    }
};
```
讲真，这道题一遍过，让我有点不可思议呢。
