题目：
==
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

分析;
==
最原始的买卖股票那个题只允许买卖一次，但本题允许多次买卖，所以只要每次比较前后大小如果第二天大于当前天的价格就将差值加入记录结果的变量里。

代码：
==
```C
int maxProfit(int* prices, int pricesSize) {
         int pro=0;
        for (int i=0;i<pricesSize-1;i++) {
            if (prices[i]<prices[i+1]) {
                pro+=prices[i+1]-prices[i];
            }
        }
        return pro;
}
```
