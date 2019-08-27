# 牛牛的闹钟

## :question:题目描述
牛牛总是睡过头，所以他定了很多闹钟，只有在闹钟响的时候他才会醒过来并且决定起不起床。从他起床算起他需要X分钟到达教室，上课时间为当天的A时B分，请问他最晚可以什么时间起床。     
>输入描述:
每个输入包含一个测试用例。
每个测试用例的第一行包含一个正整数，表示闹钟的数量N(N<=100)。
接下来的N行每行包含两个整数，表示这个闹钟响起的时间为Hi(0<=A<24)时Mi(0<=B<60)分。
接下来的一行包含一个整数，表示从起床算起他需要X(0<=X<=100)分钟到达教室。
接下来的一行包含两个整数，表示上课时间为A(0<=A<24)时B(0<=B<60)分。
数据保证至少有一个闹钟可以让牛牛及时到达教室。

>输出描述:
输出两个整数表示牛牛最晚起床时间。

>示例:
输入
3 
5 0 
6 0 
7 0 
59 
6 59
输出
6 0

## :bulb:解决思路
处理数据，把所有的时间转换为分钟单位，按照分钟大小反向排序再逐个查找符合条件的时间

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main(void){
    int N;
    int Hi, Mi;
    int X;
    int A, B, late_time;
    vector<int> time;
    
    cin>>N;
    for(int i = 0; i < N; i++) {
        cin>>Hi>>Mi;
        time.push_back(Hi*60+Mi);
    }
    cin>>X;
    cin>>A>>B;
    late_time = A * 60 + B;
    sort(time.rbegin(), time.rend());
    for(int t : time){
        if(t + X <= late_time){
            cout<<t/60<<' '<<t%60;
            break;
        }
    }
    return 0;
}
```
[:arrow_left:上一题:矩形重叠](RectangleOverlap.md)
[:arrow_right:下一题:牛牛的背包问题](NiuniuKnapsack.md)