# 回文字符串

## :question:题目描述
最大回文子串是被研究得比较多的一个经典问题。最近月神想到了一个变种，对于一个字符串，如果不要求子串连续，那么一个字符串的最大回文子串的最大长度是多少呢。

>输入描述:
每个测试用例输入一行字符串（由数字0-9，字母a-z、A-Z构成），字条串长度大于0且不大于1000。

>输出描述:
输出该字符串的最长回文子串的长度。（不要求输出最长回文串，并且子串不要求连续）

>示例
输入
adbca
输出
3
说明
因为在本题中，不要求回文子串连续，故最长回文子串为aba(或ada、aca)

## :bulb:解决思路
虽然是在讲回文，但实际上是一道动态规划题目，dp[i][j]表示从i-j的特殊回文字符串长度最大值，如果s[i]等于s[j]，dp[i][j] = d[i+1][j-1]+2，否则为dp[i+1][j],dp[i][j-1]中的较大值。

## :pencil2:代码
```c++
#include <iostream>
#include <string>
#include <vector>
using namespace std;
int main(void){
    string s;
    cin>>s;
    int N = s.length();
    vector<vector<int>> dp(N, vector<int>(N, 0));
    for(int i = 0; i < N; ++i){
        dp[i][i] = 1;
        for(int j = i-1; j >= 0; --j){
            if(s[j] == s[i])
                dp[j][i] = dp[j+1][i-1] + 2;
            else
                dp[j][i] = max(dp[j+1][i], dp[j][i-1]);
        }
    }
    cout<<dp[0][N-1]<<endl;
    return 0;
}
```
[:arrow_left:上一题:字符串排序](SortString.md)
[:arrow_right:下一题:latex爱好者](Typesetting.md)