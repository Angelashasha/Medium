题目：
==
Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s. If there isn't one, return 0 instead.

For example, given the array [2,3,1,2,4,3] and s = 7,
the subarray [4,3] has the minimal length under the problem constraint.

分析：
==
给定一个整数和一个数组，找到一个子数组使其和等于给定的这个值。我这次居然想到了二分法，分别左边和右边出发,来找两个数恰好等于给定的整数，并且我用到了sort，那这样我就意识到了错误，题目中说连续的子数组，我排序之后数组顺序就被打乱了啊，那就无所谓连续了，而且也没说一定是两个数的子数组啊。依然贴一下我不成熟的错误代码。
```C++
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        int l=nums.size();
    sort(nums.begin(),nums.end());
        int left=0;
        int right=l-1;
        while(left<right){
            if(nums[left]+nums[right]<s)
                left++;
            else if(nums[left]+nums[right]>s)
                right--;
            else
                return 2;
        }
        return 0；
    }
};
```
依然是定义两个变量left和right，分别记录子数组的左右的边界位置，然后我们让right向右移，直到子数组和大于等于给定的整数或者right达到数组末尾，此时我们更新最短距离，并且将left向右移一位，然后从sum中减去移去的值，一直重复上面的步骤，直到right到达末尾，且left到达临界位置，即要么到达边界，要么再往右移动，和就会小于给定值。
```C++
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        if (nums.empty()) return 0;
        int left=0,right=0,sum=0,len=nums.size(),res=len+1;
        while (right<len) {
            while (sum<s&&right<len) {
                sum+=nums[right++];
            }
            while (sum>=s) {
                res=min(res,right-left);
                sum-=nums[left++];
            }
        }
        return res==len+1?0:res;
        
    }
};
```
