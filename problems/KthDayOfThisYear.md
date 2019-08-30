# 今年的第几天

## :question:题目描述
输入年、月、日，计算该天是本年的第几天。    
输入：    
包括三个整数年(1<=Y<=3000)、月(1<=M<=12)、日(1<=D<=31)。    
输出：    
输入可能有多组测试数据，对于每一组测试数据， 输出一个整数，代表Input中的年、月、日对应本年的第几天。 

>输入描述:
1990 9 20

>输出描述:
263

## :bulb:解决思路
用大小为12的数组存储12个月份的天数(2月份平年28天)，以5月1号为例，需要计算5月份之前的4个月的总天数，也就是i从0到3，所以循环终止的条件为i < month-1，注意求是否为瑞年的判断公式`year%100 && !(year%4) || !(year%400)`,year%100为0表示整除100，&&左边为false，所以需要||右边为true也就是year整除400才算瑞年，否则只需要year整除4，注意最后为瑞年需要加上2月份多出来的一天。

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int year, month, day, res;
    int m[12] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    cin>>year>>month>>day;
    res = day;
    bool leapyear = year%100 && !(year%4) || !(year%400);
    for(int i = 0; i < month-1; ++i){
        res += m[i];
    }
    if(leapyear && month > 2)
        ++res;
    cout<<res<<endl;
    return 0;
}
```
[:arrow_left:上一题:字符串长度最大乘积](MaxProductOfStrLen.md)
[:arrow_right:下一题:数字序列第n位的值](#)