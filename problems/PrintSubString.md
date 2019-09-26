# 输出指定长度子串

## :question:题目描述
给定一个字符串，输出所有指定长度为n的子串，没有则输出-1

>输入描述:
输入第一行一个字符串，如：“1234567890”
输入第二行一个数字是n，如5

>输出描述:
输出所有长度为n的子串，如“12345”，“23456”，“34567”，“45678”，“56789”

## :bulb:解决思路
使用`std::string::substr`，第一个参数表示开始的位置，第二个参数表示子串长度，对于这道题再适用不过，注意对n的考虑以及for循环中输出格式的细节

## :pencil2:代码
```c++
#include <iostream>
#include <string>
using namespace std;
int main(void){
    string s;
    int n, len;
    getline(cin, s);
    cin>>n;
    len = s.length();
    //n <= 0没有考虑导致80%通过率
    if(n > len || n <= 0){
        cout<<-1<<endl;
        return 0;
    }
    for(int i = 0; i + n <= len; ++i){
        cout<<s.substr(i, n);
        if(i + n < len)
            cout<<' ';
    }
    cout<<endl;
    return 0;
}
```
[:arrow_left:上一题:possible sentences](#)
[:arrow_right:下一题:链表合并](MergeLinkedList.md)