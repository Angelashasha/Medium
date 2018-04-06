题目：
==
Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

For example:

Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].

分析：
==
这个题是Single Number的升级版，可以用异或运算得到两个数进行按位异或之后的结果，将结果与其补码进行按位与运算，即diff&=-diff，这样diff就变成了仅有1个1，其它位置都为0的数，并且那个1就是a和b第一个不相同的位置，这样就能区分开a和b了。把数组中的每一个数都与diff按位进行与运算，相同的数一定与其中一个数进行异或运算，而两个特殊的数也一定不与同一个数进行运算，所以最终就可以得出结果。

代码：
==
```C++
class Solution {
public:
    vector<int> singleNumber(vector<int>& nums) {
        vector<int> ret(2,0);
    int diff=0;
    for (int i=0; i<nums.size(); i++) {
        diff^=nums[i];
    }
    diff&=-diff;
    for (int i=0; i<nums.size(); i++) {
        if ((nums[i]&diff)==0) {
            ret[0]^=nums[i];
        }
        else {
            ret[1]^=nums[i];
        }
    }
     return ret;
    }
};
```

总结思考：
==
好吧，wrong了很多次，我终于写对了，哈哈哈哈哈哈，我怕不是个智障。（不加括号，智障一号，写不对变量名字，智障二号···）
