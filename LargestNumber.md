题目：
==
Given a list of non negative integers, arrange them such that they form the largest number.

For example, given [3, 30, 34, 5, 9], the largest formed number is 9534330.

Note: The result may be very large, so you need to return a string instead of an integer.

分析：
==
题意很明确，输入一个正整数数组，把数组里的所有数字拼接起来排成一个数，打印能拼接出的所有数字中最大的一个。在这个题目中，我们不能单纯的比较哪一个数字大，而是怎么样使拼接起来的数最大，还是要用到整数型转字符串，与昨天Maximum Swap相似，但那道题只要求我们置换两个数位，这道题是要求我们重新组成一个数，还是用字符串的方法解决比较好。将所数都做为字符串，然后进行字符串拼接，这时就可以得到字符串形式的数，然后用字符串比较，此时的比较结果与数字的比较结果是相同的。

具体思路：
==
把所有数字转化为字符串，根据字符串拼接后大小排序，然后把所有的连接起来即可。

代码：
```C++
class Solution {
public:
    string largestNumber(vector<int>& nums) {
       int l=nums.size();
        vector<string> numstr(l);
        for(int i=0;i<l;++i)
        {
            numstr[i]=to_string(nums[i]);//将每个整型数转换为字符串
        }
        sort(numstr.begin(), numstr.end(), cmp);
        string result="";
        for(int i=0;i<l;i++)
        {
            result+=numstr[i];//根据自定义的排序规则，结合后使数大的元素排在前面
         }
        if(result[0]=='0') return "0";//都是非负数，所以如果最大元素是0，那数字最大也只能是0；
        return result;
    }
    static bool cmp(string numstr1, string numstr2)
    {
        string str1=numstr1+numstr2;
        string str2=numstr2+numstr1;
        return str1>str2;
    }//依据本题排序规则，将字符串排序,这里排序的规则是使得连接字符串较大的排在前面
};
```

总结感受：
==
看到网上有很多种解法，选择了与自己想法差不多的代码作参考，一题下来，也觉得蛮有收获。这次没有掉numstr.(),哈哈
