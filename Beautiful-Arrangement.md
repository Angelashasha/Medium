题目：
==
Suppose you have N integers from 1 to N. We define a beautiful arrangement as an array that is constructed by these N numbers successfully if one of the following is true for the ith position (1 <= i <= N) in this array:

The number at the ith position is divisible by i.
i is divisible by the number at the ith position.

分析：
==
如果整数1到N的排列，第i个数满足下列规则之一，则称该排列为“美丽排列”：第i个位置的数字可以被i整除；i可以被第i个位置的数字整除。给定数字N，要求有多少个美丽排列。nums数组标记是否被访问过，当下标为1时计数器加一，最终返回计数器数值。

代码：
==
```C++
class Solution {
public:
    int countArrangement(int N) {
         nums.resize(N+1);//设置大小
        cntA(N);
        return cnt;
    }
    int cnt= 0;
    vector<bool> nums;
    void cntA(int index) {
        if (index == 1) {
            cnt++;
        }
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] == false && (i % index == 0 || index % i == 0)) {
                nums[i] = true;
                cntA(index-1);
                nums[i] = false;
            }
        }
    }
};
```
