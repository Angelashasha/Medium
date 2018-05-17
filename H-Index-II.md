题目：
==
Given an array of citations in ascending order (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.
According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than hcitations each." 
```
Example:
Input: citations = [0,1,3,5,6]
Output: 3 
Explanation: [0,1,3,5,6] means the researcher has 5 papers in total and each of them had 
             received 0, 1, 3, 5, 6 citations respectively. 
             Since the researcher has 3 papers with at least 3 citations each and the remaining 
             two with no more than 3 citations each, his h-index is 3.
```
分析：
==
这道题与之前的H指数差不多，不同的是这次给出的数组是排序后的，根据经验应该用二分查找法，最先初始化left和right为0和len-1，然后取中间值mid，比较citations[mid]和len-mid做比较，如果前者大，则right移到mid之前，反之right移到mid之后，终止条件是left>right，最后返回len-left即可

代码：
==
```C++
class Solution {
public:
    int hIndex(vector<int>& citations) {
         int l=citations.size(),left=0,right=l-1;
         while(left<=right) 
         {
            int mid=0.5*(left+right);
            if(citations[mid]==l-mid) 
                return l-mid;
            else if(citations[mid]>l-mid) 
                right=mid-1;
            else 
                left=mid+1;
        }
        return l-left;
    }
};
```
