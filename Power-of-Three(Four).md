题目：
==
ⅠGiven an integer, write a function to determine if it is a power of three.
ⅡGiven an integer (signed 32 bits), write a function to check whether it is a power of 4.

分析:
==
两个题目都很简单，在给定的数能够整除指定的数的情况下，就一直除以指定的数，如果最后余数为1，就返回true，反之，返回false。

代码：
==
```C
bool isPowerOfThree(int n) {
    while(n&&n%3==0)
        n=n/3;
    if(n==1)
        return true;
    return false;
}
```
```C
bool isPowerOfFour(int num) {
    while(num&&num%4==0)
        num/=4;
    if(num==1)
        return true;
    return false;
}
```
