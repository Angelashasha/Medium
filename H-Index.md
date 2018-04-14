题目：
==
Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."

For example, given citations = [3, 0, 6, 1, 5], which means the researcher has 5 papers in total and each of them had received 3, 0, 6, 1, 5 citations respectively. Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, his h-index is 3.

Note: If there are several possible values for h, the maximum one is taken as the h-index.

好吧，我承认此处需要翻译。给定一个数组，记载了某研究人员的文章引用次数（每篇文章的引用次数都是非负整数），编写函数计算该研究人员的h指数。

根据维基百科上对h指数的定义：“一名科学家的h指数是指在其发表的N篇论文中，有h篇论文分别被引用了至少h次，其余N-h篇的引用次数均不超过h次”。

例如，给定一个数组citations = [3, 0, 6, 1, 5]，这意味着该研究人员总共有5篇论文，每篇分别获得了3, 0, 6, 1, 5次引用。由于研究人员有3篇论文分别至少获得了3次引用，其余两篇的引用次数均不超过3次，因而其h指数是3。

注意：如果存在多个可能的h值，取最大值作为h指数。

分析：
==
找到一个数，他前面的所有数小于等于他，后面的数大于等于他。好啊，我的第一想法是中位数，于是sort排序，根据注意如果存在多个那就返回最大的那个，那么我就想要是偶数个，我就直接返回后面那个大的就行了呗，于是我的代码是酱紫的。
```C++
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int l=citations.size();
        sort(citations.begin(),citations.end());
        int index=l/2;
             return citations[index];
   }
};
```
runtimeerror,我想了很久，终于明白我错在哪里了，如果一个数组为2 2 3 4 5 6，按照我的逻辑，返回的是4，也就是说应当有四篇论文至少有四篇引文，但事实上在这个数组里只有三个符合此要求的。我看了看别人的，根据题意可将条件描述为一个区域，一条过原点的直线，一个正方形区域，当整个数组从大到小遍历刚刚到正方形区域与直线交点处时，即为所求值。

代码：
==
```C++
class Solution {
public:
    int hIndex(vector<int>& citations) {
      int l=citations.size();
   sort(citations.begin(), citations.end(), [](const int &a, const int &b){return a > b; });
        int i=0;
        for (; i<l;i++)
            if (citations[i] <= i)
                break;
        return i;
   }
};
```
