题目：
==
Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.
```
Example 1:
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]
```
```
Example 2:
Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```
分析：
==
题目要求螺旋输出给定的数组，事实上，螺旋始终重复四个遍历过程：向右遍历（列递增），向下遍历（行递增），向左遍历（列递减），向上遍历（行递减）。但在螺旋遍历的过程中，行列的上下边界一直在变，所以我们用四个变量，rowBegin, rowEnd, colBegin, colEnd，通过这四个变量来记录数组行列边界。需要注意的一点是，我们在向左遍历和向上遍历时，要看要遍历的行或者列是否存在，避免重复。

代码:
==
```C++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
         vector<int> ret;  
        if (matrix.empty()) return ret;  
        int row=matrix.size(),col=matrix[0].size(); 
        int rowBegin=0,colBegin=0;  
        int rowEnd=row-1,colEnd=col-1;  
        while (rowBegin<=rowEnd &&colBegin<=colEnd)  
        {   
            //向右列递增遍历  
            for (int j = colBegin; j <= colEnd; j++)  
            {  
                ret.push_back(matrix[rowBegin][j]);  
            }  
            rowBegin++;               
            //向下行递增遍历  
            for (int i = rowBegin; i <= rowEnd; i++)  
            {  
                ret.push_back(matrix[i][colEnd]);  
            }  
            colEnd--;   
            if (rowBegin <= rowEnd)  //这是防止重复的重要判断  
            {  
                //向左列递减遍历  
                for (int j = colEnd; j >= colBegin; j--)  
                {  
                    ret.push_back(matrix[rowEnd][j]);  
                }  
                  
            }  
            rowEnd--;   
            if (colBegin <= colEnd)  //这也是防止重复的重要判断  
            {  
                //向上行递减遍历  
                for (int i = rowEnd; i >= rowBegin; i--)  
                {  
                    ret.push_back(matrix[i][colBegin]);  
                }  
            }  
            colBegin++;
         }  
          
         return ret;  
    }
};
```
