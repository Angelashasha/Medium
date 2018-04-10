题目：
==
Your are given an array of integers prices, for which the i-th element is the price of a given stock on day i; and a non-negative integer fee representing a transaction fee.

You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction. You may not buy more than 1 share of a stock at a time (ie. you must sell the stock share before you buy again.)

Return the maximum profit you can make.
```
Example 1:
Input: prices = [1, 3, 2, 8, 4, 9], fee = 2
Output: 8
Explanation: The maximum profit can be achieved by:
Buying at prices[0] = 1
Selling at prices[3] = 8
Buying at prices[4] = 4
Selling at prices[5] = 9
The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.
```
分析：
==
这道题与之前的买卖股票题差不多，不过这道题有交易费，我一开始的想法与前两题的一样，就是看如果后面一天股票升了就卖出，不过多了一步就是判断加上手续费卖出后有没有利润，若有，则将交易后的计入利润中。所以我的代码是这样的：
```C
int maxProfit(int* prices, int pricesSize, int fee) {
    int  maxPro=0;
    for(int i=0;i<pricesSize-1;i++)
    {
        if(prices[i]<prices[i+1])
        {
            int tmp=prices[i+1]-prices[i]-fee+maxPro;
                maxPro=max(tmp,maxPro);
        }
    }
    return maxPro;
}
int max(int a,int b)
{
    if(a<b)
        return b;
    else
        return a;
}
```
但是wrong answer，我回头看了一下买卖股票Ⅱ，发现自己当时的算法是求后面元素大于前面元素的所有差的和。我就想到一个问题，有没有可能在一个数组中，最大的数与最小的数的差值大于前面这种做法所求得的差之和呢？于是我就写了一个很low的代码来解决这个问题。
```C++
#include<iostream>
#include<algorithm>
using namespace std;
int main()
{
    int nums[4];
 for(int i=0;i<4;i++)
    cin>>nums[i];
    int tmp=0;
    for(int i=0;i<3;i++)
    {
        if(nums[i+1]>nums[i])
    tmp+=nums[i+1]-nums[i];
    }
     sort(nums,nums+4);
    int tmp2=nums[3]-nums[0];
    if(tmp>tmp2)
     cout<<"差之和最大"<<endl;
    else if(tmp==tmp2)
        cout<<"可能一样大"<<endl;
        else
            cout<<"最大差最大"<<endl;
        return 0;
}
```
我测试了我所能想到的情况，发现，只要是数组不是纯递减数组，那么差之和大于或等于最大数与最小数的差。如果是这样的话，那我股票Ⅱ的那道题的做法就没有问题了。

所以这个题目我错在了那里呢：按照刚才的想法，差之和大于等于最大的差值，那两者去掉同样的手续费，自然还是差之和的做法得到的利润最大，而问题就在于这里，我们差之和，多次交易，手续费就多，而找较大的差值并不一定会有很多次交易，两种方式交易次数不同，自然不能用上面的方式进行比较。而事实上，的确是找较大差值时进行交易比较划算。
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
         int profit=0;  
        int curProfit=0;  
        int minP=prices[0];  
        int maxP=prices[0];  
        int i;  
        for(i=1;i<prices.size();i++){  
            minP=min(minP,prices[i]);  
            maxP=max(maxP,prices[i]);  
            curProfit=max(curProfit,prices[i]-minP-fee);  
            if((maxP-prices[i])>=fee){
                profit+=curProfit;  
                curProfit=0;  
                minP=prices[i];  
                maxP=prices[i];  
            }  
        }  
        return profit+curProfit;
    }
};
```
关键是找到一个最大股票价后是不是能够卖掉stock，重新开始寻找买入机会。比如序列1 3 2 8，如果发现2小于3就完成交易买1卖3，此时由于fee=2，（3-1-fee）+(8-2-fee)<(8-1-fee)，所以说明卖早了，令max是当前最大price，当（max-price[i]>=fee）时可以在max处卖出，且不会存在卖早的情况，再从i开始重新寻找买入机会.curProfit记录了当前一次交易能得到的最大收益，只有当maxP-prices[i]>=fee时，才将curProfit累加到总的收益中。最后一次交易不需要考虑是否早卖了，所以直接累加最后一次的curProfit然后返回结果即可。
