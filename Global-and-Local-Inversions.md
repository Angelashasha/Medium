题目：
==
We have some permutation A of [0, 1, ..., N - 1], where N is the length of A.

The number of (global) inversions is the number of i < j with 0 <= i < j < N and A[i] > A[j].

The number of local inversions is the number of i with 0 <= i < N and A[i] > A[i+1].

Return true if and only if the number of global inversions is equal to the number of local inversions.
```
Example 1:

Input: A = [1,0,2]
Output: true
Explanation: There is 1 global inversion, and 1 local inversion.
```
```
Example 2:

Input: A = [1,2,0]
Output: false
Explanation: There are 2 global inversions, and 1 local inversion.
```
分析：
==
给定排列A，判断其全局逆序对的个数和局部逆序对的个数是否相等。局部逆序对是指：0 <= i < N 并且 A[i]>A[i+1]；全局逆序对是指：i < j 并且 0 <= i < j < N 并且 A[i] > A[j]。
局部反转属于全局反转，所以说这个数组里只允许出现相邻的两个数字是大小反转的，其他的若是间隔的两个数字，就只能是从小到大的顺序。如果A的大小<=2，直接return true即可；否则，对于第i+2个数字来说，必须保证前i个数字都比第i+2个数字小，所以要求前i个数字的最大值小于i+2处的数字即可。所以用maxn标记前i个数字中最大的，让它和A[i+2]比较，如果出现了maxn比A[i+2]大的情况，则说明不可能满足条件，返回false，否则最后返回true。

代码：
==
```C
bool isIdealPermutation(int* A, int ASize) {
     if (ASize<=2) return true;  
        for (int i = 0, maxn = -1; i <ASize- 2; i++) {  
            maxn = max(maxn, A[i]);  
            if (maxn > A[i+2]) return false;  
        }  
        return true;  
}
int max(int a,int b)
{
    if(a>b)
        return a;
    else
        return b;
}
```
