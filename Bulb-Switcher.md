题目：
==
There are n bulbs that are initially off. You first turn on all the bulbs. Then, you turn off every second bulb. On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb. Find how many bulbs are on after n rounds.

Example:

Given n = 3. 

At first, the three bulbs are [off, off, off].
After first round, the three bulbs are [on, on, on].
After second round, the three bulbs are [on, off, on].
After third round, the three bulbs are [on, off, off]. 

So you should return 1, because there is only one bulb is on.

分析：
==
n个灯一开始全都是关闭的，第一步把所有的灯打开，接下来每i步，每i个灯改变其开闭状态，第n步，只改变在最后一个灯的开闭状态，求最后剩下几个灯亮着。我一开始理解成了第i步改变第i个灯的状态，写着写着看到最后说第n步只改变最后一个灯的状态，才意识到自己想错了，哇。我现在想的就是，把所有灯泡放在一个数组里，每i个改变状态，只要下标是i的倍数就改变状态，最后再转变最后一个灯的开闭状态，我是通过1和0来分别表示开闭，最后遍历，记录数组中为1的元素个数即可。这样的话我在实现怎么找到下标是i倍数那一步一直想不明白，于是我就去网上百度了一下，发现这道题居然是找规律的题目，找到了规律，问题迎刃而解了。

具体思路：
==
按照题目思路，多找几个数来试一试，会发现凡是平方数的灯泡最后都会亮着，所以这道题就变成了找n以内的平方数。

代码：
==
```C
int bulbSwitch(int n) {
    int sum=1;
    while (sum*sum<=n) sum++;
      return sum-1;
}
```

总结感受：
==
找规律，也让我目瞪狗呆啊。不过这也让我认识到，不能一味就题论题，规规矩矩按题意一步一步利用代码实现，要去想实质问题在哪里，一针见血才好，我在这个题目中的想法就过于简单，或许能解此题，但遇到类似的，稍微一变动可能就行不通了，而发现内在规律才是真正有价值的。
