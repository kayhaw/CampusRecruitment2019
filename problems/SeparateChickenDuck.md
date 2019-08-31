# 鸡鸭分类问题

## :question:题目描述
农场有n只鸡鸭排为一个队伍，鸡用“C”表示，鸭用“D”表示。当鸡鸭挨着时会产生矛盾。需要对所排的队伍进行调整，使鸡鸭各在一边。每次调整只能让相邻的鸡和鸭交换位置，现在需要尽快完成队伍调整，你需要计算出最少需要调整多少次可以让上述情况最少。例如：CCDCC->CCCDC->CCCCD这样就能使之前的两处鸡鸭相邻变为一处鸡鸭相邻，需要调整队形两次。

>输入描述:
输入一个长度为N，且只包含C和D的非空字符串。

>输出描述:
使得最后仅有一对鸡鸭相邻，最少的交换次数

>示例:
输入 CCDCC
输出 2

## :bulb:解决思路
只有两种类型，只需要考虑把一个字母挪到最左边或者最右边即可，挪C到最左边等价于挪D到最右边，以挪到左边为例，这里又要考虑是挪C到左边交换少还是挪D交换少，为此都计算出来然后取较小值即可，每次挪动次数等于当前位置减去左边已经拍好的C或者D的队列的末尾位置。

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int i = 0, l = 0, r = 0, resC = 0, resD = 0;
    char c;
    while((c = cin.get()) != '\n'){
        if(c == 'C')
            resC += i-l, ++l;
        else
            resD += i-r, ++r;
        ++i;
    }
    cout<<(resC < resD ? resC : resD)<<endl; 
    return 0;
}
```
[:arrow_left:上一题:最小代价爬楼梯](DPClimbStair.md)
[:arrow_right:下一题:比特币最佳买卖时机](MakeMoneyFromBitcoin.md)