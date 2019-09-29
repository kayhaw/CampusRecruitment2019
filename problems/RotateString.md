# 字符串旋转

## :question:题目描述
给定两字符串A和B，如果能将A从中间某个位置分割为左右两部分字符串（都不为空串），并将左边的字符串移动到右边字符串后面组成新的字符串可以变为字符串B时返回true。
例如：如果A=‘youzan’，B=‘zanyou’，A按‘you’‘zan’切割换位后得到‘zanyou’和B相同返回true。

>输入描述:
2个不为空的字符串(说明:输入一个字符串以英文分号";"分割为2个字符串)
例如:youzan;zanyou 即为A=‘youzan’，B=‘zanyou’

>输出描述:
输出true或false(表示是否能按要求匹配两个字符串)

>示例
输入：youzan;zanyou
输出：true

## :bulb:解决思路
将其中字符串A复制拼接在自身尾部形成新串AA，看B是否在AA中包含，**注意，也有可能B是A的子串，所以先要判断长度是否相等**

## :pencil2:代码
```c++
#include <iostream>
#include <string>
using namespace std;
int main(void){
    string A, B;
    char c;
    while((c = cin.get()) != ';')
        A.append(1, c);
    while((c = cin.get()) != '\n')
        B.append(1, c);
    //首先要判断长度是否相同
    if(A.length() != B.length())
        cout<<"false"<<endl;
    else
        A += A, cout<<(A.find(B) == string::npos ? "false" : "true")<<endl;
    return 0;
}
```
[:arrow_left:上一题:有序矩阵中第K小的元素](KthMinNumInMatrix.md)
[:arrow_right:下一题:数组移动跳跃](#)