题目:
===
Rotate an array of n elements to the right by k steps.
For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

分析：
===
解决这个问题有很多方法，我觉得很简单的一种就是，先把先n-k个翻转，再把后k个翻转，最后全部反转一遍。

代码：
===
```C++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if(nums.empty()||(k %= nums.size())==0) return;
        int l=nums.size();
        reverse(nums.begin(),nums.begin()+n - k);
        reverse(nums.begin()+n-k, nums.end());
        reverse(nums.begin(),nums.end());
    }
};
```
最直接的解决方案：
```C++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        vector<int> tmp=nums;
        for (int i=0;i<nums.size();i++) {
            nums[(i+k)%nums.size()]=tmp[i];
        }
    }
};
```
我还在网上看到一个我觉得蛮有意思的写法：不断的交换元素位置来实现最终的旋转。
```C++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if(nums.empty()) return;
        int l= nums.size();
        int start= 0;   
        while (l&&(k%=l)) {
            for (int i=0;i<k;i++) {
                swap(nums[i+start],nums[l-k+i+start]);
            }
            l-= k;
            start+= k;
        }
    }
};
```
