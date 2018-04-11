题目：
==
On a staircase, the i-th step has some non-negative cost cost[i] assigned (0 indexed).

Once you pay the cost, you can either climb one or two steps. You need to find minimum cost to reach the top of the floor, and you can either start from the step with index 0, or the step with index 1.
```
Example 1:
Input: cost = [10, 15, 20]
Output: 15
Explanation: Cheapest is start on cost[1], pay that cost and go to the top.
```
```
Example 2:
Input: cost = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]
Output: 6
Explanation: Cheapest is start on cost[0], and only step on 1s, skipping cost[3].
```
分析：
==
题目说每次可以跨1或2级台阶，可以任意从第一级或者第二级开始，条件是当跨到每个台阶时，需要付当前台阶的费用，求登上最高层台阶的最少花费。定义一个变量记录跨上当前台阶后的费用，将未跨上此级台阶的记录给另外一个变量，遍历所有台阶，每次都选择当前费用少的方案，最终到达最高层时输出两个变量中较小的一个即为最少费用。

代码：
==
```C
int minCostClimbingStairs(int* cost, int costSize) {
    int a=0,b=0;
    for(int i=0;i<costSize;i++)
    {
        int tmp=min(a,b)+cost[i];
        a=b;
        b=tmp;
    }
    return min(a,b);
}
int min(int a,int b)
{
    if(a>=b)
        return b;
    else
        return a;
}
```
