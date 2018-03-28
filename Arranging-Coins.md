题目：
==
You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.

Given n, find the total number of full staircase rows that can be formed.

n is a non-negative integer and fits within the range of a 32-bit signed integer.
```
Example 1:

n = 5

The coins can form the following rows:
¤
¤ ¤
¤ ¤

Because the 3rd row is incomplete, we return 2.
Example 2:

n = 8

The coins can form the following rows:
¤
¤ ¤
¤ ¤ ¤
¤ ¤

Because the 4th row is incomplete, we return 3.
```
分析：
==

题目很简单了，给定一个整数n，第i行有i个数，看能排列几个完整的行。通过for循环和if语句，如果n值大于当前行所需要的数字那么row+1，n值相应减少对应的数，直到n不能排成一行就跳出循环，返回row。

代码：
==
```C
int arrangeCoins(int n) {
    int row=0;
    for(int i=1;;i++)
    {
        if(n>=i)
        { 
            row+=1;
            n-=i;
        }  
        else
            break;
    }
    return row;
}
```
反思：
==
很简单的题，我硬是把n-=i写成了n-=1，妈耶，wrong了好几次，好气哦。
