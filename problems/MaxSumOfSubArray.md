# 求连续子数组的最大和

## :question:题目描述
一个非空整数数组，选择其中的两个位置，使得两个位置之间的数和最大。
如果最大的和为正数，则输出这个数；如果最大的和为负数或0，则输出0。

>输入描述:
3,-5,7,-2,8

>输出描述:
13

## :bulb:解决思路
cur表示当前数字之前的最大连续子数组和，cur大于0更新cur为cur+当前数，否则cur小于0只会成为累赘，令cur为0表示从当前数开始重新求连续子数组之和，将cur和全局的最大和maximum比较并更新。

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
#include <sstream>
#include <string>
#include <algorithm>
using namespace std;
int main(void){
    int tmp, cur = 0, maximum = 0;
    string str;
    char ch;
    vector<int> nums;
    getline(cin, str);
    istringstream is(str);
    while(is>>tmp){
        nums.push_back(tmp);
        is>>ch;
    }
    for(int num : nums){
        cur = max(cur, 0) + num;
        maximum = max(maximum, cur);
    }
    cout<<maximum<<endl;
    return 0;
}
```
[:arrow_left:上一题:解析加减法运算](SimpleAddMinus.md)
[:arrow_right:下一题:字符串长度的最大积](MaxProductOfStrLen.md)