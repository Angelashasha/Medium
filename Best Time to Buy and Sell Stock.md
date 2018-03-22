题目：
==
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.
```
Example 1:

Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
```
```
Example 2:

Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```

分析：
==
（愚蠢的我通过例子才勉强知道这个题的股票买卖是怎么回事）买在卖的前面，所以遍历，每个元素后面的所有元素与当前元素做差，找出最大的差，如果这个差是个正值就返回，否则返回0.

代码：
==
```C
int maxProfit(int* prices, int pricesSize) {
    int max=-1;
    for(int i=0;i<pricesSize;i++){
        for(int j=i+1;j<pricesSize;j++){
            max=max>(prices[j]-prices[i])?max:(prices[j]-prices[i]);
        }
    }
    if(max>0) return max;
    else
        return 0;
}
```

总结：
==
第一遍的时候i从1开始循环，所以情况不全出错了，改过来就没问题呢
