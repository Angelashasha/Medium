题目：
==
Suppose you have a random list of people standing in a queue. Each person is described by a pair of integers (h, k), where h is the height of the person and k is the number of people in front of this person who have a height greater than or equal to h. Write an algorithm to reconstruct the queue.
```
Example
Input:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]
Output:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]
```
分析：
==
讲真，我不得不吐槽这个题目让我压根不知道是怎么排，我只能从例子入手，题目说给出每个人的身高h和排在他前面身高不小于他的人数K，根据例子，显然同时根据k和h来找排序规律最有助于解决问题。在h相同时，队列要按照k从小到大排列，于是如果h最大的先返回到定义的返回数组中，那么序列会按照k进行排列，依次加入h次大的序列到返回数组，到任意位置i，h如果比i的h大，或者h相同并且k小于i的k，那么就应当插在i前，也就是说插入位置是i的k。

代码：
==
```C++
class Solution {
public:
   static bool cmp(pair<int,int> &a,pair<int,int>&b)
   {
       return (a.first>b.first||(a.first==b.first&&a.second<b.second));
   }
    vector<pair<int,int> > reconstructQueue(vector<pair<int,int> > &people)
    {
        vector<pair<int,int> > ret;
        int l=people.size();
        if(!l)  return ret;
        sort(people.begin(),people.end(),cmp);
        for(int i=0;i<l;i++)
         ret.insert(ret.begin()+people[i].second,people[i]);
        return ret;
    }
};
```
总结体会：
==
对我来说有点费解，我自己一步一步写出来试了试才明白，这是我第一次练习这种题，还是有些收获的。
