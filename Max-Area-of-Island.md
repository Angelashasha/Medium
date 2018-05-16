题目：
==
Given a non-empty 2D array grid of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)
```
Example 1:
[[0,0,1,0,0,0,0,1,0,0,0,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,1,1,0,1,0,0,0,0,0,0,0,0],
 [0,1,0,0,1,1,0,0,1,0,1,0,0],
 [0,1,0,0,1,1,0,0,1,1,1,0,0],
 [0,0,0,0,0,0,0,0,0,0,1,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,0,0,0,0,0,0,1,1,0,0,0,0]]
Given the above grid, return 6. Note the answer is not 11, because the island must be connected 4-directionally.
```
```
Example 2:
[[0,0,0,0,0,0,0,0]]
Given the above grid, return 0.
```
分析：
==
题目要求，1代表着陆地，4个直接相连的，包括垂直或者一行这种情况，即视为一个岛屿，要求我们找到岛屿的最大面积。统计给定的数组中1的个数，出现最多的就是答案，同时我通过help函数来确定是否为1.

代码：
==
```C++
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        int ret=0;  
        for (int i=0;i<grid.size();i++)  
        {  
            for (int j= 0;j < grid[0].size();j++)  
            {  
                if (grid[i][j])  
                {  
                    ret= max(ret, help(grid, i, j));  
                }  
            }  
        }  
        return ret;  
    }  
  
    int help(vector<vector<int>>& grid,int i,int j)  
    {  
        if (i < 0 || i >= grid.size() || j < 0 || j >= grid[0].size()) return 0;  
        if (grid[i][j])  
        {  
            grid[i][j]=0;  
            return  1+help(grid,i,j+1)+help(grid,i+1,j)+help(grid,i,j-1)+help(grid,i-1,j);  
        }  
        return 0;  
    }
};
```
