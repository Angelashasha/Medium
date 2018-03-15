题目：
==
Given a non-negative integer c, your task is to decide whether there're two integers a and b such that a2 + b2 = c. 
```
Example 1:

Input: 5
Output: True
Explanation: 1 * 1 + 2 * 2 = 5

Example 2:

Input: 3
Output: False
```

分析：
==
给定一个非负数，判断这个数是否能够写成两个数平方的和。一开始有点混乱，后来就想到之前做过很多次从两边往中间凑数的题，一下就有了思路。如果这个数本身就是个平方数，那么就是相当于他开方后与0相加，从给定的这个数的平方与0相加开始，看会不会有两个数的平方的和等于给定的这个数。

代码：
==
```C
bool judgeSquareSum(int c) {
    int a=0,b=sqrt(c);
    while(a<=b){
        if(a*a+b*b==c)  return true;
        else if(a*a+b*b>c)  b--;
        else a++;
    }
    return false;
}
```
