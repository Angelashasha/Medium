题目:
==
A sequence of number is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, these are arithmetic sequence:

1, 3, 5, 7, 9
7, 7, 7, 7
3, -1, -5, -9
The following sequence is not arithmetic.

1, 1, 2, 5, 7

A zero-indexed array A consisting of N numbers is given. A slice of that array is any pair of integers (P, Q) such that 0 <= P < Q < N.

A slice (P, Q) of array A is called arithmetic if the sequence:
A[P], A[p + 1], ..., A[Q - 1], A[Q] is arithmetic. In particular, this means that P + 1 < Q.

The function should return the number of arithmetic slices in the array A.


Example:

A = [1, 2, 3, 4]

return: 3, for 3 arithmetic slices in A: [1, 2, 3], [2, 3, 4] and [1, 2, 3, 4] itself.

分析：
==
（题目真长）其实就是给定一组数字，返回这串数字中能够构成等差数列的子串的数目。这是一个与数学有关的问题，自然是先总结一下规律。当我们遍历数组，发现下一个数字可以加入子串等差数列中，我们要知道的就是这一个元素的加入对于所有等差数列子串数目的影响。利用一个比较简单的等差数列，观察就能发现每增加一个可以与前面构成等差的数，等差数列数目之差就是[1,2, 3, 4, 5……]这个序列，也就是说，每次增加一个等差数列的元素，总的等差数列的数目就会增加[1,2, 3, 4, 5……]中对应的数值。

具体思路：
==
设置一个变量more来表示等差数组增加的数目，对应着[1,2, 3, 4, 5……]这个序列，遍历，如果数组的下一个元素可以加入到等差数列中，more就加1，然后总的数目count就增加more。如果数组下一个元素不能加入到等差数列中，more就重置为0即可。这样的话通过一次遍历就可以得到最终结果了。

代码：
==
```C
int numberOfArithmeticSlices(int* A, int ASize) {
     int count=0;
     int more=0;
    for (int i=2;i<ASize;i++){
       if(A[i-1]-A[i]==A[i-2]-A[i-1])
       {more++;
         count=count+more;}
        else 
           more=0;
    }
    return count;
}
```
