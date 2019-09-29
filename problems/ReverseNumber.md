# 整数的倒数

## :question:题目描述
整数的倒数

>输入描述:
输入一个整数x

>输出描述:
把x倒序输出

>示例1
输入：123
输出：321

>示例2
输入：-123
输出：-321

## :bulb:解决思路
简单一点，用字符串接受输入而不是整型，注意当首字符为'-'保留位置，不能翻转

## :pencil2:代码
```c++
#include <iostream>
#include <algorithm>
using namespace std;
int main(void){
    string s;
    cin>>s;
    if(s[0] == '-')
        reverse(s.begin()+1, s.end());
    else
        reverse(s.begin(), s.end());
    cout<<s<<endl;
    return 0;
}
```
[:arrow_left:上一题:括号配对问题](ParenthesesMathch.md)
[:arrow_right:下一题:字符串加法](BinaryNumberAdd.md)