# a/b

## :question:题目描述
求a/b的小数表现形式。如果a可以整除b则不需要小数点。如果是有限小数，则可以直接输出。如果是无限循环小数，则需要把小数循环的部分用"()"括起来。    

>输入描述:
两个整数a和b，其中
0 <= a <= 1000 000
1 <= b <= 10 000

>输出描述:
一个字符串，该分数的小数表现形式

>示例:
输入 1 7
输出 0.(142857)

## :bulb:解决思路
求无限循环小数的循环部分，a%b循环乘10除以b,余数×10再对b取模，保存余数到哈希表中，当余数再一次出现时，说明开始循环，注意m[a]表示小数部分前面的非循环部分

## :pencil2:代码
```c++
#include <iostream>
#include <map>
#include <vector>
#include <iterator>
using namespace std;
int main(void){
    int a, b, t = 0;
    map<int, int> m;
    vector<int> v;
    bool flag = false;
    while(cin>>a>>b){
        cout<<a/b;
        a = a % b;
        if(!a){
            cout<<endl;
            continue;
        }
        cout<<'.';
        while(a){
            if(m.count(a))  break;
            v.push_back(a * 10 / b);
            m[a] = t++;
            a= a * 10 % b;
        }
        if(!a){
            copy(v.begin(), v.end(), ostream_iterator<int>(cout));
        }else{
            for(int i = 0; i < m[a]; i++) cout << v[i];
                cout << "(";
            for(int i = m[a]; i < t; i++) cout << v[i];
                cout << ")";
        }
        cout<<endl;
        m.clear();
        v.clear();
        flag = false;
        t = 0;
    }
    return 0;
}
```
[:arrow_left:上一题:数字序列第n位的值](NthValue.md)
[:arrow_right:下一题:最小代价爬楼梯](DPClimbStair.md)