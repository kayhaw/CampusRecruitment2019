# 字符串加法

## :question:题目描述
输入两个字符串a和b，字符串内容为二进制数字，求两个字符串相加的结果，加法计算方法以二进制方式计算，并返回对应的字符串结果。要求程序尽可能的高效。

>输入描述:
输入两个字符串，如"1101", "1100"

>输出描述:
"11001"

>示例
输入：1101 1100
输出：11001

## :bulb:解决思路
- 将输入的二进制字符串转为整型，相加后的整型结果再转为对应的二进制字符串。**缺点：当输入二进制字符串长度大于32/64时会整型相加溢出**
- 二进制字符串从尾向前相加，复杂度O(n)

## :pencil2:代码
```c++
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
int main(void){
    int i = 0, j = 0, s;
    string a , b, c;
    cin>>a>>b;
    for(char c : a){
        i *= 2;
        if(c == '1')
            i += 1;
    }
    for(char c : b){
        j *= 2;
        if(c == '1')
            j += 1;
    }
    s  = i + j;
    while(s){
        c.append(1, s%2+'0');
        s /= 2;
    }
    reverse(c.begin(), c.end());
    cout<<c<<endl;
    return 0;
}
```
[:arrow_left:上一题:整数的倒数](ReverseNumber.md)
[:arrow_right:下一题:有序矩阵中第K小的元素](KthMinNumInMatrix.md)