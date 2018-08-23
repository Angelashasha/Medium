题目：
==
Initially, there is a Robot at position (0, 0). Given a sequence of its moves, judge if this robot makes a circle, which means it moves back to the original place.
The move sequence is represented by a string. And each move is represent by a character. The valid robot moves are R (Right), L (Left), U (Up) and D (down). The output should be true or false representing whether the robot makes a circle.

```
Example 1:
Input: "UD"
Output: true
```
```
Example 2:
Input: "LL"
Output: false
```
分析：
==
一个机器人位于原点处，以一串字符串来记录机器人的运动路径，U、D分别表示上行下行，L、R则表示左右行走，要求我们通过字符串来判断机器人最终会不会回到原点。我的想法就是只要左右走的步数和上下走的步数分别相等即可。

解决方案：
==
像分析上说的，左右上下步数分别相等，也就是说如果向左走了多少步那么就应该向右走了多少步才能保证左右方向上回到原位置，同理上下方向也是这样，所以设置四个变量分别记录上下左右左右走的步数即可，通过判断是否u与d、l与r都相等，若满足，则可以回到原点。

代码：
==
```C++
class Solution {
public:
    bool judgeCircle(string moves) {
        int len=moves.size();
        int u=0,d=0,l=0,r=0;
        for(int i=0;i<len;i++)
        {
            
            if(moves[i]=='U')
                u++;
            else if(moves[i]=='D')
                d++;
            else if(moves[i]=='L')
                l++;
            else
                r++;
        }
        if(u==d&&l==r)
            return true;
        return false;
    }
};
```
