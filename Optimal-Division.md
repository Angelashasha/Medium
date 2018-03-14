题目：
==
Given a list of positive integers, the adjacent integers will perform the float division. For example, [2,3,4] -> 2 / 3 / 4.

However, you can add any number of parenthesis at any position to change the priority of operations. You should find out how to add parenthesis to get the maximum result, and return the corresponding expression in string format. Your expression should NOT contain redundant parenthesis.

```
Example:

Input: [1000,100,10,2]
Output: "1000/(100/10/2)"
Explanation:
1000/(100/10/2) = 1000/((100/10)/2) = 200
However, the bold parenthesis in "1000/((100/10)/2)" are redundant, 
since they don't influence the operation priority. So you should return "1000/(100/10/2)". 

Other cases:
1000/(100/10)/2 = 50
1000/(100/(10/2)) = 50
1000/100/10/2 = 0.5
1000/100/(10/2) = 2
```

Note:

    The length of the input array is [1, 10].
    Elements in the given array will be in range [2, 1000].
    There is only one optimal division for each test case.

分析：
==
给定一组正整数，相邻整数之间用除号来连接，在其中加入括号来改变运算顺序，也就改变了除数，求运算结果最大的时候的方案，返回此时的表达式。数组的第一个元素一定是被除数，第二个元素一定是
除数，要使结果最大，就要使除数最小，于是我希望除数是第二个元素到最后一个元素一直相除最后的商，那么这个值其实就是第一个数与除了第二个数以外的其他元素相乘再除以第二个元素

代码：
==
```C++
class Solution {
public:
    string optimalDivision(vector<int>& nums) {
        int l=nums.size();
        if(l==1) {
            return to_string(nums[0]);
        }
        if(l==2) {
            return to_string(nums[0]) +"/"+to_string(nums[1]);
        }
        string temp=to_string(nums[1]);
        string ret=to_string(nums[0])+"/";
        for (int i=2;i<l;i++) {
            temp+="/";
            temp+=to_string(nums[i]);
        }
         ret+="(" + temp + ")";
        return ret;
    }
};
```

总结感受：
==
思路是很清晰的，但在代码实现的过程中就不是那么easy了，一开始并没有考虑只有一个数或者两个数的情况，在哪个位置加括号也是很清楚的，但是怎么通过表达式写出来我还是参考了一下网上的，发现自己的想法真的是弱爆了，我想到的只是如何找到最大的结果，但我没有想到直接用字符型的表达，利用to_string函数直接把表达式写出再在指定位置加括号就好了，学到了！
