# 最小代价爬楼梯

## :question:题目描述
你需要爬上一个N层的楼梯，在爬楼梯过程中， 每阶楼梯需花费非负代价，第i阶楼梯花费代价表示为cost[i]， 一旦你付出了代价，你可以在该阶基础上往上爬一阶或两阶。你可以从第 0 阶或者 第 1 阶开始，请找到到达顶层的最小的代价是多少。N和cost[i]皆为整数，且N∈[2,1000]，cost[i]∈ [0, 999]。

>输入描述:
输入为一串半角逗号分割的整数，对应cost数组，例如
10,15,20

>输出描述:
输出一个整数，表示花费的最小代价

>示例:
输入 1,100,1,1,1,100,1,1,100,1
输出 6

## :bulb:解决思路
DP动态规划问题，dp[i]表示到第i级台阶花费的代价，根据题意一开始就可以在第0级或者第1级台阶，所以dp[0]=d[1]=0，到达第i级台阶，无非就两种情况，从第i-1级爬上来的，从第i-2级爬上来的，从第i-1级爬上来的花费代价就是dp[i-1]+cost[i-1]，从第i-2级爬上来的花费代价就是dp[i-2]+cost[i-2]，取其较小值。

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
#include <sstream>
using namespace std;
int main(void){
    int x;
    char c;
    string s;
    vector<int> v;
    cin>>s;
    s += ',';
    istringstream iss(s);
    while(iss>>x>>c){
        v.push_back(x);
    }
    vector<int> dp(v.size()+1, 0);
    for(int i = 2; i <= v.size(); ++i)
        dp[i] = min(dp[i-2]+v[i-2], dp[i-1]+v[i-1]);
    cout<<dp.back()<<endl;
    return 0;
}
```
[:arrow_left:上一题:a/b](ADivideB.md)
[:arrow_right:下一题:鸡鸭分类问题](SeparateChickenDuck.md)