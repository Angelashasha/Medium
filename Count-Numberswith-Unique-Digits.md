题目：
==
Given a non-negative integer n, count all numbers with unique digits, x, where 0 ≤ x < 10n.

Example:
Given n = 2, return 91. (The answer should be the total numbers in the range of 0 ≤ x < 100, excluding [11,22,33,，44,55,66,77,88,99])

分析：
==
这道题让我们找一个范围内的各个数位上数字不相同的数。想到了排列组合，10以内的数都符合题意，如果是100以内也就是两位数，那么第一个数位上有9种选择，第二个数位上9种选择，也就是81个数，以此类推，f（n）=9 * 9 * 8 *···· * （9-n+2）

代码：
==
```C
int countNumbersWithUniqueDigits(int n) {
        if(n==0) return 1;  
        if(n==1) return 10;  
        int way=9,sum=10;  
        for(int i=2;i<=n;i++)  
        {  
            way=way*(9-i+2);  
            sum+=way;  
        } //从两位数开始计算有多少数符合要求 
        return sum;  
}
```

总结感受：
==
emmm，就是一个数学问题了，知道排列组合就很简单了。
