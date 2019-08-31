# 爱吃喵粮的小招喵

## :question:题目描述
小招喵喜欢吃喵粮。这里有 N 堆喵粮，第 i 堆中有 p[i] 粒喵粮。喵主人离开了，将在 H 小时后回来。小招喵可以决定她吃喵粮的速度 K （单位：粒/小时）。每个小时，她将会选择一堆喵粮，从中吃掉 K 粒。如果这堆喵粮少于 K 粒，她将吃掉这堆的所有喵粮，然后这一小时内不会再吃更多的喵粮。小招喵喜欢慢慢吃，但仍然想在喵主人回来前吃掉所有的喵粮。返回她可以在 H 小时内吃掉所有喵粮的最小速度 K（K 为整数）。 

>输入描述:
第一行输入为喵粮数组，以空格分隔的N个整数
第二行输入为H小时数

>输出描述:
最小速度K

>示例:
输入
3 6 7 11
8
输出 4

## :bulb:解决思路
H至少要大于等于猫粮堆数，等于时最小速度为猫粮中最大的容量，大于时最小速度low为sum/H-1，最大速度high为sum/(H-N)+1，-1/+1扩大范围，然后在low和high之间使用二分法查找，这里使用从最小的速度开始循环遍历

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
using namespace std;
int main(void){
    vector<int> v;
    int x, H, sum = 0, max = 0;
    int low, high, hour = 0;
    while(cin>>x){
        v.push_back(x);
        sum += x;
        max = max > x ? max : x;
        if(cin.get() == '\n')
            break;
    }
    cin>>H;
    if(H == v.size()){
        cout<<max<<endl;
        return 0;
    }
    //两边+1，-1扩大搜索范围
    low = sum/H-1;
    high = sum/(H-v.size())+1;
    for(int i = low; i <= high; ++i){
        hour = 0;
        for(int j = 0; j < v.size(); ++j){
            hour += v[j] / i;
            if(v[j] % i)
                ++hour;
        }
        if(hour <= H){
            cout<<i<<endl;
            break;
        }
    }
    return 0;
}
```
[:arrow_left:上一题:比特币最佳买卖时机](MakeMoneyFromBitcoin.md)
[:arrow_right:下一题:X游戏](XGame.md)