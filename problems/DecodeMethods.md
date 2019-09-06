# 解码方法

## :question:题目描述
一条包含字母 A-Z 的消息通过以下方式进行了编码：
>'A' -> 1
'B' -> 2
...
'Z' -> 26

给定一个只包含数字的非空字符串，请计算解码方法的总数。 

>输入描述:
一串编码过的数字，比如12

>输出描述:
解码方法的总数

>示例:
输入 12
输出 2
说明 12可以解码成“AB”，“A，B"这两种

## :bulb:解决思路
动态规划的使用，dp[i]表示**从头开始**到长度为i部分的编码字符串的解码方案，编码方法从最后一个数字往前面看，要么最后一个数字解码为1-9对应的字母，要么最后两个数字解码为10-26，这样dp[i]分解为dp[i-1]和dp[i-2]，也就是dp[i]=dp[i-1]+dp[i-2]，注意if条件部分的判断，解码一位数不能是0，解码两位数不能是超过27，首位不能是0

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    string s;
    int len;
    cin>>s;
    len = s.length();
    int *dp = new int[len+1]{};
    dp[0] = 1;
    for(int i = 1; i <= len; ++i){
        if(s[i-1] != '0')
            dp[i] += dp[i-1];
        if(i >= 2 && s[i-2] == '1' || s[i-2] == '2' && s[i-1] < '7')
            dp[i] += dp[i-2];
    }
    cout<<dp[len]<<endl;
    delete dp;
    return 0;
}
```
[:arrow_left:上一题:员工考勤记录](AttendanceRecord.md)
[:arrow_right:下一题:漂流船问题](MinNumOfBoats.md)