题目：
==
Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

Solve it without division and in O(n).

For example, given [1,2,3,4], return [24,12,8,6].

Follow up:
Could you solve it with constant space complexity? (Note: The output array does not count as extra space for the purpose of space complexity analysis.)


分析：
==
题目要求将给定数组的每一位元素值转化为除了它本身外的其他元素相乘，且要求不能用除法（其实第一反应就是除法呢，忧桑）。那么，我们可以先从左往右遍历数组得到每个元素左边所有元素的乘积，再从右往左遍历得到每个元素右边所有元素的乘积，在第二遍遍历时，就直接与第一遍遍历的每个元素相乘。

代码：
==
```C++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
     int l=nums.size();      
     vector<int> result(l,1);  
     int left=1;
     int right=1;
        //从左到右累乘，数组每个元素存放的值为它左边的所有数的累乘值。（由于第一个的左边和最后一个元素的右边没有元素，所以让其乘1，即left和right）
        for(int i = 0;i<l;i++){
            result[i]=left;
            left=left*nums[i];
        }
        //同理，从右到左让数组的每一个元素累乘它右边的元素。
        for(int j=l-1;j>=0;j--){
            result[j]=result[j]*right;
            right=right*nums[j];
        }
        return result;
    }
};
```

总结感受：
==
很少会从两边往中间来解题，其实这就好比我们推导恒等式，有时从左向右，有时从右向左，有时推导到中间步骤，都需要灵活思考。
