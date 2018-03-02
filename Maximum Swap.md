题目：
==
Given a non-negative integer, you could swap two digits at most once to get the maximum valued number. Return the maximum valued number you could get.

Example 1: Input: 2736 Output: 7236

Explanation: Swap the number 2 and the number 7.

Example 2: Input: 9973 Output: 9973

Explanation: No swap.

Note: The given number is in the range [0, 10^8]

分析：
==
这道题目中给我们一个数字，我们可以置换该数字中的任意两位，返回置换后的最大值，如果当前数字就是最大值，则不必置换，直接返回原数。一开始我的想法是，找到各个数位上最大的一个数，把他放在最高位上，我只是单纯地这样想，一时间又不知道怎么相互交换，当我突然想到之前转字符串的那种方法时，我又发现要是最大的数有两个怎么办？于是，最终我打算所有的数位都两两交换一下，找最大的不就行了，这大概是最暴力的解决方式吧

代码：
==
```C++
class Solution {
public:
    int maximumSwap(int num) {
        string str=to_string(num);//整数型转换为字符串
        int max=num;
        int l=str.size();
        for(int i=0;i<l;i++) {
            for (int j=i+1;j<l;j++) {
                swap(str[i], str[j]);
                max=max>stoi(str)?max:stoi(str);//交换两数位并储存较大的数
                swap(str[i], str[j]);//换回原来的数方便进行其他的数位置换；
            }
        }
        return max;
    }
};
```

总结感受：
==
第一次出现的主要错误就是没有把换过去的数位换过来就直接进行下一次置换数位了。

注：
==
vs环境下：

stoi函数默认要求输入的参数字符串是符合int范围的[-2147483648, 2147483647]，否则会runtime error。

atoi函数则不做范围检查，若超过int范围，则显示-2147483648（溢出下界）或者2147483647（溢出上界）。

stoi头文件：<string>,c++函数
atoi头文件:<cstdlib>,c函数

此题中说了数字num的范围，一定不会溢出，所以可用stoi。
