
题目：
==
Given scores of N athletes, find their relative ranks and the people with the top three highest scores, who will be awarded medals: "Gold Medal", "Silver Medal" and "Bronze Medal".
```
Example 1:
Input: [5, 4, 3, 2, 1]
Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
Explanation: The first three athletes got the top three highest scores, so they got "Gold Medal", "Silver Medal" and "Bronze Medal". 
For the left two athletes, you just need to output their relative ranks according to their scores.
```
分析：
==
题目给定一组数，要求求出相对排名，并且前三名可分别得到金银铜牌，后面是名次。利用堆来排序，建立一个优先队列，把分数和对应坐标位置放入队列中，然后就会自动根据分数高低进行排序，然后我们从顶端开始将数据一个一个取出，因为会保存数据在原数组的位置，所以我们直接把他存到ret中相应的位置即可，用一个变量cnt来记录其名次，然后得到前三名有奖牌，后面就都是名次数即可。
（代码的具体实现参考了网上的，确实让我又熟悉了一下这个优先队列的用法。）

代码：
==
```C++
class Solution {
public:
    vector<string> findRelativeRanks(vector<int>& nums) {
        int l=nums.size();
        int cnt=1;
        vector<string> ret(l,"");
        priority_queue<pair<int, int>> q;
        for(int i=0;i<l;i++) 
        {
            q.push({nums[i],i});
        }
        for(int i=0;i<l;i++) 
        {
            int tmp=q.top().second; 
                q.pop();
            if(cnt==1) ret[tmp] = "Gold Medal";
            else if(cnt==2) 
                ret[tmp]="Silver Medal";
            else if(cnt==3) 
                ret[tmp]="Bronze Medal";
            else 
                ret[tmp]=to_string(cnt);
            cnt++; 
        }
        return ret;
    }
};
```
