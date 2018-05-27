题目：
==
You are standing at position 0 on an infinite number line. There is a goal at position target.

On each move, you can either go left or right. During the n-th move (starting from 1), you take n steps.

Return the minimum number of steps required to reach the destination.
```
Example 1:
Input: target = 3
Output: 2
Explanation:
On the first move we step from 0 to 1.
On the second step we step from 1 to 3.
```
```
Example 2:
Input: target = 2
Output: 3
Explanation:
On the first move we step from 0 to 1.
On the second move we step  from 1 to -1.
On the third move we step from -1 to 2.
```
分析：
==
题目要求从原点向数轴数轴两边移动，第n次走n步，每次都是可以向左走或者向右走，直至到达目标数字，求所需最小步数。数轴是对称的，所以我们只需求解target的绝对值的步数取反即可。然后有一个问题就是，我们按部就班一步一加，那么就会出现和大于target的情况，如何补救呢？当超过目标值的差值d为偶数时，只要将第d/2步的距离取反，就能得到目标值，此时的步数即为到达目标值的步数。那么，如果d为奇数时，且当前为第n步，那么我们看下一步n+1的奇偶，如果n+1为奇数，那么加上n+1再做差，得到的差值就为偶数了，问题解决，如果n+1为偶数，那么还得加上n+2这个奇数，才能让差值为偶数，这样就多加了两步。定义两个变量ret和sum，sum用以，如果与target差值为奇数我们就循环中的操作，而当偶数返回ret即可

代码：
==
```C++
class Solution {
public:
    int reachNumber(int target) {
         target=abs(target);
        int ret=0;
        int sum=0;
        while(sum<target||(sum-target)%2==1) 
        {
            ret++;
            sum+=ret;
        }
        return ret;
    }
};
```
