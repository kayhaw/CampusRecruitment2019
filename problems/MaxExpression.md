# 表达式求值

## :question:题目描述
 今天上课，老师教了小易怎么计算加法和乘法，乘法的优先级大于加法，但是如果一个运算加了括号，那么它的优先级是最高的。例如：
```
1+2*3=7
1*(2+3)=5
1*2*3=6
(1+2)*3=9
```
现在小易希望你帮他计算给定3个数a，b，c，在它们中间添加"+"， "*"， "("， ")"符号，能够获得的最大值。   

>输入描述:
一行三个数a，b，c (1 <= a, b, c <= 10)

>输出描述:
能够获得的最大值

>示例:
输入
1 2 3
输出
9

## :bulb:解决思路
就3个数，情况也就只有4种，全部计算出来输出最大值即可

## :pencil2:代码
```c++
#include <iostream>
#include <algorithm>
using namespace std;

int main(void){
    int a, b, c;
    cin>>a>>b>>c;
    cout<<max(a+b+c, max(a*(b+c), max(a*b*c, (a+b)*c)));
    return 0;
}
```
[:arrow_left:上一题:整理房间](WhichHeap.md)
[:arrow_right:下一题:塔](AdjustTower.md)