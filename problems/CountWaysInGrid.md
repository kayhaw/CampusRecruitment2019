# 方格走法

## :question:题目描述
有一个X*Y的网格，小团要在此网格上从左上角到右下角，只能走格点且只能向右或向下走。请设计一个算法，计算小团有多少种走法。给定两个正整数int x,int y，请返回小团的走法数目。

>输入描述:
输入包括一行，空格隔开的两个正整数x和y，取值范围[1,10]。

>输出描述:
输出一行，表示走法的数目

>示例:
输入 
3 2
输出
10

## :bulb:解决思路
$X*Y$网格从左上角走到右下角的走法等于组合数$C_{x+y}^{x}$，计算这个组合数有两种方式：
1. 将其视为动态规划问题，注意生命定义dp数组的大小为$(X+1)$*$(Y+1)$，因为最后要求`dp[X][Y]`,并且注意初始化所有值为1
2. 直接通过函数计算$C_{x+y}^{x}=\frac{(x+y)!}{x!*y!}$

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
using namespace std;
int main(void){
    int X, Y;
    cin>>X>>Y;
    vector<vector<int>> dp(X+1,vector<int>(Y+1, 1));
    for(int i = 1; i < X+1; ++i){
        for(int j = 1; j < Y+1; ++j){
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }
    cout<<dp[X][Y]<<endl;
    return 0;
}
```
[:arrow_left:目的地最短步数](MinStepsToArrive.md)
[:arrow_right:下一题:possible sentences](#)