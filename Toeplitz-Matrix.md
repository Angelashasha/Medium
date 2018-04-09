题目：
==
A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.
```
Example 1:

Input: matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]
Output: True
Explanation:
1234
5123
9512

In the above grid, the diagonals are "[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]", and in each diagonal all elements are the same, so the answer is True.
```
```
Example 2:

Input: matrix = [[1,2],[2,2]]
Output: False
Explanation:
The diagonal "[1, 2]" has different elements.
```
分析：
==
根据题意，所谓托普利兹矩阵，就是主对角元元素全部相同，给出一个矩阵，要求判断是否为托普利兹矩阵。判断的方法很简单，正难则反，只要主对角元上有不同的元素那就不是，我一开始的问题是没有找到行和列的表示方式，想明白了问题也就解决了。

代码：
==
```C++
class Solution {
public:
    bool isToeplitzMatrix(vector<vector<int>>& matrix) {
       int m=matrix.size() ;
       int n=matrix[0].size() ;
          for(int i=0;i<m-1;i++){
              for(int j=0;j<n-1;j++){
                  if (matrix[i][j]!=matrix[i+1][j+1])
                      return false ;
             }
         }
         return true ;
    }
};
```
