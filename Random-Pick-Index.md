题目：
==
Given an array of integers with possible duplicates, randomly output the index of a given target number. You can assume that the given target number must exist in the array.

Note:
The array size can be very large. Solution that uses too much extra space will not pass the judge.
```
Example:
int[] nums = new int[] {1,2,3,3,3};
Solution solution = new Solution(nums);
// pick(3) should return either index 2, 3, or 4 randomly. Each index should have equal probability of returning.
solution.pick(3);
// pick(1) should return 0. Since in the array only nums[0] is equal to 1.
solution.pick(1);
```
分析：
==
题目要求我们找到一个目标数字的下标，如果这个目标数字出现了多次，随机输出一个下标。定义两个变量，计数器cnt和返回结果ret，遍历数组，如果不等于目标数字就跳过，等于目标数字计数器加一，然后我们在0到计数器cnt的值的范围内随机生成一个数字，如果是0，就将i的值赋给ret，返回即可。

代码:
==
```C++
class Solution {
public:
    Solution(vector<int> nums) {
        v=nums;
    }
    
    int pick(int target) {
        int cnt=0,ret;
        for (int i = 0; i < v.size(); i++) {
            if (v[i] !=target) continue;
                  cnt++;
            if (rand()%cnt==0) 
                ret=i;
        }
        return ret;
    }
private:
     vector<int> v;
};
```
关于rand（）函数：
==
```
一、rand()

rand()函数用来产生随机数，但是，rand()的内部实现是用线性同余法实现的，是伪随机数，由于周期较长，因此在一定范围内可以看成是随机的。

rand()会返回一个范围在0到RAND_MAX（32767）之间的伪随机数（整数）。

在调用rand()函数之前，可以使用srand()函数设置随机数种子，如果没有设置随机数种子，rand()函数在调用时，自动设计随机数种子为1。随机种子相同，每次产生的随机数也会相同。

rand()函数需要的头文件是：<stdlib.h>

rand()函数原型：int rand(void);

使用rand()函数产生1-100以内的随机整数：int number1 = rand() % 100;

二、srand()

srand()函数需要的头文件仍然是：<stdlib.h>

srand()函数原型：void srand (usigned int seed);

srand()用来设置rand()产生随机数时的随机数种子。参数seed是整数，通常可以利用time(0)或geypid(0)的返回值作为seed。

使用rand()和srand()产生1-100以内的随机整数:srand(time(0));

    int number1 = rand() % 100;

三、使用rand()和srand()产生指定范围内的随机整数的方法

“模除+加法”的方法

因为，对于任意数，0<=rand()%(n-m+1)<=n-m

因此，0+m<=rand()%(n-m+1)+m<=n-m+m

因此，如要产生[m,n]范围内的随机数num，可用：

int num=rand()%(n-m+1)+m;

其中的rand()%(n-m+1)+m算是一个公式，记录一下方便以后查阅。

比如产生10~30的随机整数：

srand(time(0));

int a = rand() % (21)+10;
```
