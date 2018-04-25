==
Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]

The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

分析：
==
题目给出一个三角形数阵，要求寻找从三角形顶部达到底部的最小路径和，在这个过程中，从上一行的某个位置只能移动到下一行的与其相邻位置。从底部到顶部,记录从底部到顶部每一步的路径，最后返回最先记录的总路径即可。

代码：
==
```C++
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        int l=triangle.size(); 
        if(l==0) return 0;
        if(l==1) return triangle[0][0];    
        vector<int> ret=triangle[l-1];
        for(int i=l-2;i>=0;i--)  
        {  
            for(int j=0;j<triangle[i].size();j++)  
            {  
                ret[j]=min(triangle[i][j]+ret[j],triangle[i][j]+ret[j+1]);  
            }  
        }  
        return ret[0];  
    }
};
```
