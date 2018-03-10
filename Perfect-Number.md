题目：
==
We define the Perfect Number is a positive integer that is equal to the sum of all its positive divisors except itself.
Now, given an integer n, write a function that returns true when it is a perfect number and false when it is not.

Example:

Input: 28
Output: True
Explanation: 28 = 1 + 2 + 4 + 7 + 14

分析：
==
根据题意，所谓完美数字，就是这个数字要等于除本身之外的所有因子之和，要求我们判断给出的数字是否为完美数字。1不用说，肯定是，那么其余因子中较小的一半就从2到n的平方之间产生，如果可以被n整除，那么就与设置的和的变量继续相加，最后比较和与n是否相等，返回相应的结果。

代码：
==
```C++
bool checkPerfectNumber(int num) {
    int sum=1;
    if(num==1)
        return false;
    for(int i=2;i<=sqrt(num);i++){
        if(num%i==0)
            sum=sum+i+num/i;
        if(i*i==num)
            sum=sum-i;
    }
    if(sum==num)
        return true;
     return false;
}
```

总结感受：
==
一开始傻了，把整数所有的因子都当成小于其平方了，运行以后发现不对，就想到自己只加上了比较小的那个因子，改过来以后，还是不合适啊，仔细看了看，如果这个数刚好可以开平方得整数，那我就多加了一遍这个因子，修改后就过了。
