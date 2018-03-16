题目：
==
 Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note:

    1 is typically treated as an ugly number.
    Input is within the 32-bit signed integer range. 

分析：
==
所谓丑陋数就是其质数因子只能是2,3,5，所以做法就是不停地除以这几个因数，如果最后得1，那就是丑陋数。

代码：
==
```C++
class Solution {
public:
    bool isUgly(int num) {
    if(num<=0) return false;
    else if(num<=2) return true;
    while(num%2==0) num/=2;
    while(num%3==0) num/=3;
    while(num%5==0) num/=5;
     if(num==1) return true;
    return false;
    }
};
```

总结感受：
==
题目再定义丑陋数的时候说是正数且质数因子为2 3 5的，我理解成了给定的数都是正数，所以一开始没有判断小于0的情况，发现不合适又修改了一下。
