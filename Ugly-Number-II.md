题目：
==
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.

Note that 1 is typically treated as an ugly number, and n does not exceed 1690.

分析：
==
这道题的丑数和定义与之前的丑数1相同，也是可以被2 3 5整除的数就是丑数，其中1也是丑数。把已经求得的数组中的某个元素乘上2或者3或者5得到下一个应该存入数组的丑数。初始化丑数下标都为0，加入新的数后2 3 5要乘的数应当后移相应位置。

代码：
==
```C++
class Solution {
public:
    int nthUglyNumber(int n) {
      vector<int> ret(n);
        ret[0]=1;
        int i_2=0,i_3=0,i_5=0;
        int base1=2,base2=3,base3=5;
        int i=1;
        for(;i<n;i++){
            int base=min(base1,min(base2,base3));
            if(base==base1){
                ret[i]=base1;
                i_2++;
                base1=ret[i_2]*2;
            }
            if(base==base2){
                ret[i]=base2;
                i_3++;
                base2=ret[i_3]*3;
            }
            if(base==base3){
                ret[i]=base3;
                i_5++;
                base3=ret[i_5]*5;
            }
        }
        return ret[n-1];
    }
};
```

