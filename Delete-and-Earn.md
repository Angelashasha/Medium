题目：
==
Given an array nums of integers, you can perform operations on the array.

In each operation, you pick any nums[i] and delete it to earn nums[i] points. After, you must delete every element equal to nums[i] - 1 or nums[i] + 1.

You start with 0 points. Return the maximum number of points you can earn by applying such operations.
```
Example 1:
Input: nums = [3, 4, 2]
Output: 6
Explanation: 
Delete 4 to earn 4 points, consequently 3 is also deleted.
Then, delete 2 to earn 2 points. 6 total points are earned.
```
```
Example 2:
Input: nums = [2, 2, 3, 3, 3, 4]
Output: 9
Explanation: 
Delete 3 to earn 3 points, deleting both 2's and the 4.
Then, delete 3 again to earn 3 points, and 3 again to earn 3 points.
9 total points are earned.
```
分析：
==
题目给出一个数组，每次可以删除一个数字，删除的数字本身变成积分累积，同时会删除掉之前数的加1和减1的数，但是删除的数字不计入积分，求最多能获得多少积分。对于每一个数字，我们都有两个选择，拿或者不拿。如果我们拿了当前的数字，我们就不能拿之前的数字，那么当前的积分就是不拿前面的数字的积分加上当前数字之和。如果我们不拿当前的数字，那么对于前面的数字我们既可以拿也可以不拿，于是当前的积分就是拿前面的数字的积分和不拿前面数字的积分中的较大值。我们用take和not分别表示拿与不拿上一个数字，takei和noti分别表示拿与不拿当前数字，每次都要更新takei、skipi、take和skip，最后返回take和not中的大值即可。

代码：
==
```C++
class Solution {
public:
    int deleteAndEarn(vector<int>& nums) {
        vector<int> sums(10001, 0);
        int take=0,not=0;
        for (int num:nums) 
            sums[num] += num;
        for (int i=0;i<10001;i++) {
            int takei=notsums[i];
            int noti=max(not, take);
            take = takei; 
            not = skipi;
        }
        return max(not, take); 
    }
};
```
