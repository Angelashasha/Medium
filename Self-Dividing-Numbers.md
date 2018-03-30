题目：
==
A self-dividing number is a number that is divisible by every digit it contains.

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.
```
Example 1:
Input: 
left = 1, right = 22
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
```
分析：
==
根据题意，所谓的自我分裂数字就是每个数位上的数都可以被此数整除，如果某数位有零，那么这个数就不是自分裂整数了。根据题意，首先写一个函数来判断一个数是否为自分裂正数，再通过for循环，逐次找出范围内所有的自分裂整数。

代码：
==
```C++
class Solution {
public:
    vector<int> selfDividingNumbers(int left, int right) {
      vector<int> ret;
        for (int i=left;i<=right;i++) {
            if(Sdn(i))
                ret.push_back(i);
        }
        return ret;
    }
    bool Sdn(int num) {
        int tmp=num,x=0;
        while (tmp) {
            x=tmp % 10;
            if (x==0||num%x!=0)
                return false;
            tmp/=10;
        }
        return true;
    }
};
```
