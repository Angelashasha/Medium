题目：
==
Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).
```
Example 1:
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
Example 2:
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
Example 3:
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```
分析：
==
这道题让我们求数组中第三大的数，如果不存在的话那么就返回最大的数，题目中说明了这里的第三大不能和第二大相同，必须是严格的小于，而并非小于等于。所以我觉得难点就在这，我是打算排序直接找到第三大的，但是有重复的就比较麻烦。那么就换种思路，如果知道怎么求第二大的数，那么求第三大的数的思路都是一样的。那么我们用三个变量first, second, third来分别保存第一大，第二大，和第三大的数，然后我们遍历数组，如果遍历到的数字大于当前第一大的数first，那么三个变量各自错位赋值，如果当前数字大于second，小于first，那么就更新second和third，如果当前数字大于third，小于second，那就只更新third，这里还有个坑，就是初始化要用长整型long的最小值，否则当数组中有INT_MIN存在时，程序就不知道该返回INT_MIN还是最大值first了。

代码：
==
```C++
class Solution {
public:
    int thirdMax(vector<int>& nums) {
       long first=LONG_MIN,second=LONG_MIN,third=LONG_MIN;
        for (int num:nums) {
            if (num>first) {
                third=second;
                second=first;
                first=num;
            } 
            else if (num > second && num < first) {
                third = second;
                second = num;
            }
            else if (num > third && num < second) {
                third = num;
            }
        }
        return (third==LONG_MIN || third==second) ? first:third;
    }
};
```
