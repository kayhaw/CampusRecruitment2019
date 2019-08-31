# 糖果分配

## :question:题目描述
假设你是一位很有爱的幼儿园老师，想要给幼儿园的小朋友们一些小糖果。但是，每个孩子最多只能给一块糖果。对每个孩子 i ，都有一个胃口值 gi ，这是能让孩子们满足胃口的糖果的最小尺寸；并且每块糖果 j ，都有一个尺寸 sj 。如果 sj >= gi ，我们可以将这个糖果 j 分配给孩子 i ，这个孩子会得到满足。你的目标是尽可能满足越多数量的孩子，并输出这个最大数值。注意：你可以假设胃口值为正。一个小朋友最多只能拥有一块糖果。

>输入描述:
第一行输入每个孩子的胃口值
第二行输入每个糖果的尺寸
孩子数和糖果数不超过1000

>输出描述:
跳完n个格子到达终点的方法

>示例:
能满足孩子数量的最大值

## :bulb:解决思路
讲胃口值和糖果尺寸分别按照升序排序，尽量使用最小尺寸的糖果满足小朋友的胃口，使用双指针遍历，注意循环退出条件，当小朋友或者糖果遍历完后就退出。

## :pencil2:代码
```c++
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;
int main(void){
    vector<int> children, candy;
    int x, i, j;
    while(cin>>x){
        children.push_back(x);
        if(cin.get() == '\n')
            break;
    }
    while(cin>>x){
        candy.push_back(x);
        if(cin.get() == '\n')
            break;
    }
    sort(children.begin(), children.end());
    sort(candy.begin(), candy.end());
    for(i = 0, j = 0; j < candy.size() && i < children.size(); ++j){
        if(candy[j] >= children[i])
            ++i;
    }
    cout<<i<<endl;
    return 0;
}
```
[:arrow_left:上一题:跳格子游戏](JumpStair.md)
[:arrow_right:下一题:员工考勤记录](AttendanceRecord.md)