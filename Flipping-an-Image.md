题目：
==
Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.
To flip an image horizontally means that each row of the image is reversed.  

For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].
To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].
```
Example 1:
Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
```
```
Example 2:
Input: [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
Output: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
Explanation: First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]].
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
```
分析：
==
根据题意，要求把矩阵每行先倒序翻转，然后将0 1 反转，即0变成1，1变成0。这是两个步骤，我们可以按部就班的先翻转再反转。也可以一次实现，也就是说我们对矩阵每行进行从右向左的遍历，遍历过程中实现0和1的对换，并按照这样的顺序将结果储存在数组中。

代码：
==
```C++
class Solution {
public:
    vector<vector<int>> flipAndInvertImage(vector<vector<int>>& A) {
        vector<vector<int> > ret;
        for(int i=0;i<A.size();i++)
        {
            vector<int> tmp;//用以临时储存每行；
            for(int j=A[0].size()-1;j>=0;j--)
            {
                if(A[i][j])
                tmp.push_back(0);
                else
                tmp.push_back(1);
            }
           ret.push_back(tmp);//将每行0 1互换并按照从右向左的顺序储存；
        }
       return ret;
    }
};
```

