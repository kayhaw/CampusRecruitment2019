# 数字序列第n位的值

## :question:题目描述
有一个无限长的数字序列1，2，2，3，3，3，4，4，4，4，5，5，5，5，5。。。（数字序列从1开始递增，且数字k在该序列中正好出现k次），求第n项是多少。

>输入描述:
输入为一个整数n

>输出描述:
输出一个整数，即第n项的值

>示例:
输入 4
输出 3

## :bulb:解决思路
n依次减去1,2,3，...k,当n-k小于0时说明为第k项

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int n, ans = 0;
    cin>>n;
    while(n > 0){
        ++ans;
        n -= ans;
    }
    cout<<ans<<endl;
    return 0;
}
```
[:arrow_left:上一题:今年的第几天](KthDayOfThisYear.md)
[:arrow_right:下一题:a/b](ADivideB.md)