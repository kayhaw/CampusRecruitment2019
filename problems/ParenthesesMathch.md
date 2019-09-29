# 括号配对问题

## :question:题目描述
括号配对问题

>输入描述:
给定一个字符串S，请检查该字符串的括号是否配对，只含有"[", "]", "(", ")"

>输出描述:
配对，返回true
不配对，返回false

>示例
输入：abcd(])[efg
输出：false

## :bulb:解决思路
使用栈来解决问题，遍历字符串遇到"["或者"("压入栈，遇到"]"或者")"，查看当前栈顶元素是否和右括号匹配，匹配的话弹出栈顶元素，其他非括号字符直接忽略，遍历字符串后最后看栈是否为空

## :pencil2:代码
```c++
#include <iostream>
#include <stack>
using namespace std;
int main(void){
    stack<char> s;
    char c;
    while((c = cin.get()) != '\n'){
        //一开始写的是if(s.empty() && c == '[' || c== '(')
        //这里入栈跟s是否为空没关系
        if(c == '[' || c == '(')
            s.push(c);
        //一开始写的是else if(c == ']' && s.top() == '[')
        //s可能为空造溢出
        else if(c == ']'){
            if(s.empty()){
                cout<<"false"<<endl;
                return 0;
            }else if(s.top() == '[')
                s.pop();
        }
        else if(c == ')'){
            if(s.empty()){
                cout<<"false"<<endl;
                return 0;
            }else if(s.top() == '(')
                s.pop();
        }
    }
    cout<<(s.empty() ? "true" : "false")<<endl;
    return 0;
}
```
[:arrow_left:上一题:链表合并](MergeLinkedList.md)
[:arrow_right:下一题:整数的倒数](ReverseNumber.md)