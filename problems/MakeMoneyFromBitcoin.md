# 比特币最佳买卖时机

## :question:题目描述
给定一个正整数数组，它的第 i 个元素是比特币第 i 天的价格。如果你最多只允许完成一笔交易（即买入和卖出一次），设计一个算法来计算你所能获取的最大利润。注意你不能在买入比特币前卖出。 

>输入描述:
正整数数组，为以空格分隔的n个正整数

>输出描述:
最大利润

>示例:
输入 7 1 5 3 6 4
输出 5

## :bulb:解决思路
**不能在买入比特币之前卖出**，问题相当于求升序子序列的最大差值问题，首先维护一个当前最低价格min，然后根据当前价格减去最低价格得到当前价格的最大利润，并由此维护一个最大利润，即为结果。

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int x, min = 0x7fffffff, maxprofit = 0;
    while(cin>>x){
        min = (min < x) ? min : x;
        maxprofit = (maxprofit > x-min) ? maxprofit : x-min;
        if(cin.get() == '\n')
            break;
    }
    cout<<maxprofit<<endl;
    return 0;
}
```
[:arrow_left:上一题:鸡鸭分类问题](SeparateChickenDuck.md)
[:arrow_right:下一题:爱吃猫粮的小招喵](CatFood.md)