题目:
==
Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times. The algorithm should run in linear time and in O(1) space.

分析：
==
题目给出一个数组，要求我们找到出现次数超过数组长度三分之一的数组元素，也就是众数了。最初的想法是和这个题的原始题目相类似的，但是存在语法上的错误。贴上我的代码（瑟瑟发抖）
```C++
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int l=nums.size();
        int count=0;
        int majSum=0;
        for(int i=0;i<l;i++){
            if(count==0)  {
              majSum=nums[i];
               count=1;
             }
            else{
             if(majSum==nums[i])
                 count++;
             else
                 count--;
             }
            if(count==l/3)
                return majSum;
        }
    }
};
```
我已经知道了错误所在，但我想不到其他的解决方案了。于是百度了一下，发现了一种很神奇的解法：摩尔投票法。这里很重要的一点是，题目中给了一条很重要的提示，让我们先考虑可能会有多少个众数，经过举了很多例子分析得出，任意一个数组出现次数大于n/3的众数最多有两个
投票法的核心是找出两个候选众数进行投票，需要两遍遍历，第一遍历找出两个候选众数，第二遍遍历重新投票验证这两个候选众数是否为众数即可。
```C++
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
         vector<int> res;
        int m=0,n=0,cm=0,cn=0;
        for (auto &a:nums) {
            if (a==m) ++cm;
            else if (a==n) ++cn;
            else if (cm==0) m=a,cm=1;
            else if (cn==0) n=a,cn=1;
            else --cm,--cn;
        }
        cm=cn=0;
        for(auto &a:nums) {//for(auto a : b)这个for循环，可以吧b里面的数据按a的类型一个一个地读取到a中，循环一次就进入到下一个对象上
            if (a==m) ++cm;
            else if(a==n) ++cn;
        }
        if (cm>nums.size()/3) res.push_back(m);
        if (cn>nums.size()/3) res.push_back(n);
        return res;
    }
};
```
