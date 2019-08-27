# 俄罗斯方块

## :question:题目描述
小易有一个古老的游戏机，上面有着经典的游戏俄罗斯方块。因为它比较古老，所以规则和一般的俄罗斯方块不同。荧幕上一共有 n 列，每次都会有一个 1 x 1 的方块随机落下，在同一列中，后落下的方块会叠在先前的方块之上，当一整行方块都被占满时，这一行会被消去，并得到1分。有一天，小易又开了一局游戏，当玩到第 m 个方块落下时他觉得太无聊就关掉了，小易希望你告诉他这局游戏他获得的分数。     

>输入描述:
第一行两个数 n, m
第二行 m 个数，c<sub>1</sub>, c<sub>2</sub>, ... , c<sub>m</sub>，c<sub>i</sub> 表示第i个方块落在第几列
其中 1 <= n, m <= 1000, 1 <= ci <= n

>输出描述:
小易这局游戏获得的分数

>示例:
输入
3 9
1 1 2 2 2 3 1 2 3
输出
2

## :bulb:解决思路
水桶效应，获得的分数等于所有列高度的最小值

## :pencil2:代码
```c++
#include <iostream>
#include <algorithm>
using namespace std;
int main(void){
    int n, m, c;
    cin>>n;
    int* s = new int[n]();
    cin>>m;
    for(int i = 0; i < m; i++){
        cin>>c;
        s[c-1]++;
    }
    sort(s, s+n);
    cout<<s[0];
    return 0;
}
```
[:arrow_left:上一题:牛牛的背包问题](NiuniuKnapsack.md)
[:arrow_right:下一题:瞌睡](TakeANap.md)