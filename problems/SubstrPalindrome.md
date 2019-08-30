# 回文子串

## :question:题目描述
给定一个字符串，你的任务是计算这个字符串中有多少个回文子串。("回文串”是一个正读和反读都一样的字符串，比如“level”或者“noon”等等就是回文串。)具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被计为是不同的子串。可用C++,Java,C#实现相关代码逻辑 

>输入描述:
输入一个字符串S 例如“aabcb”(1 <= |S| <= 50), |S|表示字符串S的长度。

>输出描述:
符合条件的字符串有"a","a","aa","b","c","b","bcb"
所以答案:7

>示例:
输入
aabcb
输出
7

## :bulb:解决思路
解决思路类似于前面的题目“回文字符串”，使用动态规划，以空间换时间，dp[i][j]表示位置i到位置j的子串的是否为回文字符串

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
#include <string>
using namespace std;
int main(void){
    string s;
    cin>>s;
    int n = s.length(), ans = 0;
    //注意这里构造二维向量的方法
    vector<vector<bool>> dp(n, vector<bool>(n, false));
    for(int i = n-1; i>=0; --i){
        for(int j = i; j < n; ++j){
            dp[i][j] = (s[i] == s[j]) && (j-i <=2 || dp[i+1][j-1]);
            if(dp[i][j])
                ++ans;
        }
    }
    cout<<ans<<endl;
    return 0;
}
```
[:arrow_left:上一题:最少数量货物装箱问题](LeastContainer.md)
[:arrow_right:下一题:字符串压缩](CompressStringII.md)