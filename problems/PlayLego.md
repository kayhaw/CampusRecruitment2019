# 搭积木

## :question:题目描述
 小明有一袋子长方形的积木，如果一个积木A的长和宽都不大于另外一个积木B的长和宽，则积木A可以搭在积木B的上面。好奇的小明特别想知道这一袋子积木最多可以搭多少层，你能帮他想想办法吗？定义每一个长方形的长L和宽W都为正整数，并且1 <= W <= L <= INT_MAX, 袋子里面长方形的个数为N, 并且 1 <= N <= 1000000。假如袋子里共有5个积木分别为 (2, 2), (2, 4), (3, 3), (2, 5), (4, 5), 则不难判断这些积木最多可以搭成4层, 因为(2, 2) < (2, 4) < (2, 5) < (4, 5)。   

>输入描述:
第一行为积木的总个数 N
之后一共有N行，分别对应于每一个积木的宽W和长L

>输出描述:
输出总共可以搭的层数

>示例:
输入
5
2 2
2 4
3 3
2 5
4 5
输出
4

## :bulb:解决思路
按照长，宽二维进行排序，然后转为求解最长递增子序列的动态规划问题

## :pencil2:代码
```c++
#include <iostream>
#include <algorithm>
#include <utility>
#include <vector>

using namespace std;

int main(void){
    int N, W, L, len=1;
    pair<int, int> pre={0, 0};
    vector<pair<int, int>> lego;
    cin>>N;
    for(int i = 0; i < N; ++i){
        cin>>W>>L;
        lego.push_back({W, L});
    }
    vector<int> dp(N, 0);
    sort(lego.begin(), lego.end());
    dp[0] = lego[0].second;
    for(int i = 1; i < N; i++){
        if(lego[i].second >= dp[len-1]){
            dp[len++] = lego[i].second;
        }else{
            *(upper_bound(dp.begin(), dp.begin()+len, lego[i].second)) = lego[i].second;
        }
    }
    cout<<len;
    return 0;
}
```
[:arrow_left:上一题:将满二叉树转换为求和树](ConvertFBT.md)
[:arrow_right:下一题:魔法深渊](ClimbStair.md)