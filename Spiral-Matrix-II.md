题目：
==
Given a positive integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.
```
Example:
Input: 3
Output:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```
分析：
==
题目要求我们以螺旋方式生成一个n*n数组。我采用了和昨天一样的方法，用四个变量表示四个边界，通过变量变化来记录边界的移动。在这里需要注意的是，如果给定的值为0就返回空数组。一开始初始化数组，往数组中添加元素时一定要保证没有超出n的平方。

代码：
==
```C++
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        if(n==0) return vector<vector<int>>();
        vector<vector<int>> ret(n,vector<int>(n,0));
        int rowBegin=0,colBegin=0;
        int rowEnd=n-1,colEnd=n-1;
        int num=1;
        while(rowBegin<=rowEnd&&colBegin<=colEnd)
        {
            if(num<=n*n)//向右遍历，此时不变的是行标
            {
                 for(int i=colBegin;i<=colEnd;i++)
                 { ret[rowBegin][i]=num;
                  num++;
                 }                
            }
            rowBegin++;
            if(num<=n*n)//向下遍历，此时不变的是列标
            {
                for(int i=rowBegin;i<=rowEnd;i++)
                {
                    ret[i][colEnd]=num;
                    num++;
                }
            }
            colEnd--;
            if(num<=n*n)//向左遍历，此时不变的也是行标
            {
                for(int i=colEnd;i>=colBegin;i--)
                {
                    ret[rowEnd][i]=num;
                    num++;
                }
            }
            rowEnd--;
            if(num<n*n)//向上遍历，此时不变的是列标
            {
                for(int i=rowEnd;i>=rowBegin;i--)
                {
                    ret[i][colBegin]=num;
                    num++;
                }
            }
            colBegin++;           
        }
        return ret;
    }
};
```
