题目：
==
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

For example:

Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it. 

分析：
==
题目很简单了，每个数位相加知道所得数是一个个位数，返回这个个位数。直接上我简单粗暴的代码

代码：
==
```C
int addDigits(int num) {
    int g,s;
    while(num>9){
        g=num%10;
        s=num/10;
        num=g+s;
    }
    return num;
}
```

当我ac了之后，看到别人的，发现又更好的解法。

1    1

2    2

3    3


4    4

5    5

6    6

7    7

8    8    

9    9    


10    1

11    2

12    3    

13    4

14    5

15    6

16    7

17    8

18    9

19    1

20    2

每九个数一次循环，所有大于9的数的最终结果都是对9取余，那么对于等于9的数对9取余就是0了，那所以就要换用一种全部适用的写法。
```C
int addDigits(int num) {
      return (num-1)% 9+1;
}
```
这波操作，大写的服。
