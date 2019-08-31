# 跳格子游戏

## :question:题目描述
假设你正在玩跳格子（所有格子排成一个纵列）游戏。需要 跳完n 个格子你才能抵达终点。每次你可以跳 1 或 2 个格子。你有多少种不同的方法可以到达终点呢？注意：给定 n 是一个正整数。 

>输入描述:
格子数

>输出描述:
跳完n个格子到达终点的方法

>示例:
输入 2
输出 2

## :bulb:解决思路
简单的求解斐波那契数列数列，没有考虑n过大的情况

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int n, a = 0, b = 1, c;
    cin>>n;
    while(n--){
        c = a + b;
        a = c - a;
        b = c;
    }
    cout<<c<<endl;
    return 0;
}
```
[:arrow_left:上一题:X游戏](XGame.md)
[:arrow_right:下一题:糖果分配](AllocateCandy.md)