# 员工考勤记录

## :question:题目描述
给定一个字符串来代表一个员工的考勤纪录，这个纪录仅包含以下两个字符：    
'A' : Absent，缺勤    
'P' : Present，到场    
如果一个员工的考勤纪录中不超过两个'A'(缺勤),那么这个员工会被奖赏。    
如果你作为一个员工，想在连续N天的考勤周期中获得奖赏，请问有多少种考勤的组合能够满足要求

>输入描述:
考勤周期的天数N（正整数）

>输出描述:
这N天里能获得奖赏的考勤组合数

>示例:
输入 3
输出 7

## :bulb:解决思路
简单排列组合，$ans=C_n^2+C_n^1+C_n^0=n(n+1)/2+1$

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int N;
    cin>>N;
    cout<<(N+1)*N/2+1<<endl;
    return 0;
}
```
[:arrow_left:上一题:糖果分配](AllocateCandy.md)
[:arrow_right:下一题:解码方法](#)