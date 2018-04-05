题目：
==
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

Example:
For num = 5 you should return [0,1,1,2,1,2].

分析：
==
这道题给我们一个整数n，让我们统计从0到n每个数的二进制写法中的1的个数，存入一个一维数组中返回。这种问题的话，肯定是先找规律，
```
0    0000    0          i&(i-1)
-----------------------
1    0001    1          0000
-----------------------
2    0010    1          0000
3    0011    2          0010
-----------------------
4    0100    1          0000
5    0101    2          0100
6    0110    2          0100
7    0111    3          0110
-----------------------
8    1000    1          0000
9    1001    2          1000
10   1010    2          1000
11   1011    3          1010
12   1100    2          1000
13   1101    3          1100
14   1110    3          1100
15   1111    4          1110
```
这几行还不足以找到一个简明易懂的概念，于是我看大神计算了这样一行。通过这一行，我们可以看出每个i对应的1 个数都是i&(i-1)对应的值加1。

代码：
==
```C++
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> ret(num+1,0);
        for (int i=1;i<=num;i++) {
            ret[i]=ret[i&(i-1)]+1;
        }
        return ret;
    }
};
```
总结思考:
==
这个题目用别的方法也是可以做出来的，但是我还是更喜欢找规律，不过就是找规律的过程也没那么容易，多试试呗。
