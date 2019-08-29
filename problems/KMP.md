# 字符串包含

## :question:题目描述
我们定义字符串包含关系：字符串A=abc，字符串B=ab，字符串C=ac，则说A包含B，A和C没有包含关系。

>输入描述:
两个字符串，判断这个两个字符串是否具有包含关系，测试数据有多组，请用循环读入。

>输出描述:
如果包含输出1，否则输出0。

>示例
输入
abc ab
输出
1

## :bulb:解决思路
考察字符串匹配，可以使用string类的find方法，或者自己实现KMP算法，注意这里并没有确定到底谁包含谁

## :pencil2:代码
```c++
#include <iostream>
#include <string>
using namespace std;
int KMPSearch(string &text, string &pattern);
void SetLPS(string &pattern, int *next);
int main(void){
    string text, pattern;
    while(cin>>text>>pattern){
        if(KMPSearch(text, pattern) || KMPSearch(pattern, text))
            cout<<1<<endl;
        else
            cout<<0<<endl;
    }
    return 0;
}
int KMPSearch(string &text, string &pattern){
    int i = 0, j = 0;
    int tLen = text.length();
    int pLen = pattern.length();
    int *next = new int[pLen]();
    SetLPS(pattern, next);
    while(i < tLen && j < pLen){
        if(j == -1 || text[i] == pattern[j]){
            ++i;
            ++j;
        }else{
            j = next[j];
        }
    }
    delete[] next;
    return (j == pLen) ? 1 : 0;
}
void SetLPS(string &pattern, int *next){
    int pLen = pattern.length();
    next[0] = -1;
    int k = -1, j = 0;
    while(j < pLen-1){
        if(k == -1 || pattern[j] == pattern[k]){
            ++k;
            ++j;
            next[j] = k;
        }else{
            k = next[k];
        }
    }
}
```
[:arrow_left:上一题:合并数组](MergeSortedList.md)
[:arrow_right:下一题:最少数量货物装箱问题](LeastContainer.md)