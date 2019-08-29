# 字符串归一化

## :question:题目描述
通过键盘输入一串小写字母(a~z)组成的字符串。请编写一个字符串归一化程序，统计字符串中相同字符出现的次数，并按字典序输出字符及其出现次数。例如字符串"babcc"归一化后为"a1b2c2"。

>输入描述:
每个测试用例每行为一个字符串，以'\n'结尾，例如cccddecca

>输出描述:
输出压缩后的字符串ac5d2e

## :bulb:解决思路
只出现小写字母，而且按照字典排序输出，建立长度为26的数组统计即可

## :pencil2:代码
```c++
#include <iostream>
#include <string>
using namespace std;
int main(void){
    string s, res;
    int total[26] = {0};
    cin>>s;
    for(char c : s){
        ++total[c-'a'];
    }
    for(int i = 0; i < 26; ++i){
        if(total[i]){
            res.append(1, 'a'+i);
            res.append(to_string(total[i]));
        }
    }
    cout<<res;
    return 0;
}
```
[:arrow_left:上一题:善变的同伴](MostDeliciousDish.md)
[:arrow_right:下一题:字符串排序](SortString.md)