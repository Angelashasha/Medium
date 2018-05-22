题目：
==
X is a good number if after rotating each digit individually by 180 degrees, we get a valid number that is different from X.  Each digit must be rotated - we cannot choose to leave it alone.

A number is valid if each digit remains a digit after rotation. 0, 1, and 8 rotate to themselves; 2 and 5 rotate to each other; 6 and 9 rotate to each other, and the rest of the numbers do not rotate to any other number and become invalid.

Now given a positive number N, how many numbers X from 1 to N are good?
```
Example:
Input: 10
Output: 4
Explanation: 
There are four good numbers in the range [1, 10] : 2, 5, 6, 9.
Note that 1 and 10 are not good numbers, since they remain unchanged after rotating.
```
分析：
==
根据题意，将一个数字的每一位旋转180度，如果跟之前的数字不一样则是有效的，要求统计1到N中有多少这样的数字。在1到10中，3、4、7旋转后是无效的，所以我的想法就是据此写一个函数来判断是否有效，然后再一个判断计数即可。

代码：
==
```C++
class Solution {
public:
    int rotatedDigits(int N) {
          int ret=0 ;
          for(int i=1;i<=N;i++)
          {
              if (isValid(i))
                  ret++;
          }
         return ret;
     }
     bool isValid(int n)
     {
         bool flag=false ;
         while(n>0){
             if (n % 10 == 2) flag = true ;
             if (n % 10 == 5) flag = true ;
             if (n % 10 == 6) flag = true ;
             if (n % 10 == 9) flag = true ;
             if (n % 10 == 3) return false ;
             if (n % 10 == 4) return false ;
             if (n % 10 == 7) return false ;
             n/=10;
         }
         return flag ;
     }
};
```
