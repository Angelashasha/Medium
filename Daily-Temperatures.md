题目：
==
Given a list of daily temperatures, produce a list that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put 0 instead.

For example, given the list temperatures = [73, 74, 75, 71, 69, 72, 76, 73], your output should be [1, 1, 4, 2, 1, 1, 0, 0].

分析：
==
题目给出一组气温，让我们找出几天后会有比当前更暖和的天气。暴力解决不过，只能另想他法，参考了一下网上的，这道题应该使用递减栈来做，栈里只有递减元素，遍历数组，如果栈不空，且当前数字大于栈顶元素，就取出栈顶元素，由于当前数字大于栈顶元素的数字，而且一定是第一个大于栈顶元素的数，那么我们直接求出下标差就是二者的距离了，然后继续看新的栈顶元素，直到当前数字小于等于栈顶元素停止，然后将数字入栈，这样就可以一直保持递减栈，且每个数字和第一个大于它的数的距离也可以算出来了。

代码：
==
```C++
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temperatures) {
        int l=temperatures.size();
        vector<int> ret(l, 0);
        stack<int> st;
        for (int i=0;i<l;i++) 
        {
            while (!st.empty()&&temperatures[i]>temperatures[st.top()]) 
            {
                auto t=st.top(); 
                st.pop();
                ret[t]=i-t;
            }
            st.push(i);
        }
        return ret;
    }
};
```
