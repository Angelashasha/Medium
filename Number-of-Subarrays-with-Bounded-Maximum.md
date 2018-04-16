题目：
==
We are given an array A of positive integers, and two positive integers L and R (L <= R).

Return the number of (contiguous, non-empty) subarrays such that the value of the maximum array element in that subarray is at least L and at most R.

分析：
==
题目要求找有多少连续的子数组，在[L,R]之间，A[i]在L，R之间是num+=(i-j)，超过R需要记录j=i，单纯的小于L不能算，那么就拿一个k记录一下不在[L,R]的位置，然后(i-j)-(i-k+1)即可。

代码：
==
```C++
class Solution {
public:
    int numSubarrayBoundedMax(vector<int>& A, int L, int R) {
         int l=A.size();
             int num=0;
             int k=0;
             int i=0,j=-1;
             for(int i=0;i<l;i++){
                 if(A[i]>R){
                     k=i+1;
                     j=i;
                 }else if(A[i]<L){
                     num+=(i-j)-(i-k+1);
                 }else{
                     num+=(i-j);
                    k=i+1;
                 }
             }
             return num;
    }
};
```
