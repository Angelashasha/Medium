题目：
==

Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

For example, the 32-bit integer ’11' has binary representation 00000000000000000000000000001011, so the function should return 3.

分析：
==
题目要求写一个带有无符号整数的函数，返回其具有的'1'位数的个数。利用与运算，给定的数每一位都和1做与运算，如果结果不为0说明最后一位为0就直接去判断下一位，否则ret+1，最后返回ret。

代码：
==
```C
int hammingWeight(uint32_t n) {
    int ret=0;
    for(int i=0;i<32;i++)
    {
        if(n&1)
            ret++;
        n>>=1;
    }
    return ret;
}
```
