题目：
==
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

```
Example 1:
Input: [1,2,3], [1,1]
Output: 1
Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
```
```
Example 2:
Input: [1,2], [1,2,3]
Output: 2
Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```
分析：
==
题目要求分蛋糕，每个孩子都有自己可以接受的蛋糕的最小值，根据孩子的接受值将蛋糕分发，保证孩子拿到不小于自己接受程度大小的蛋糕。我最初的代码是这样的：
```C++
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        int sum=0;
        int l1=g.size(),l2=s.size();
        for(int i=0;i<l1;i++)
            for(int j=0;j<l2;j++)
                if(g[i]<=s[j])
                {
                    sum++;
                    g.erase(g.begin()+i);
                    l1--;
                }
        return sum;
    }
};
```
运行后是runtime，确实是我把解决方案想复杂了，我想的是将给出的蛋糕大小与孩子的接受值进行比较，如果可以，计数器加一，同时就把这块蛋糕删除掉，这样就避免出现同一块蛋糕分给多人，但其实完全没有这么麻烦的必要，直接排序之后再比较会方便很多。

代码：
==
```C++
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        int ret=0,j=0;
         sort(g.begin(),g.end());
         sort(s.begin(),s.end());
         for (int i=0;i<s.size();i++) {
             if (s[i]>=g[j]) {
                 ret++;
                 j++;
                 if(j>=g.size()) break;
             }
         }
         return ret;
    }
};
```
