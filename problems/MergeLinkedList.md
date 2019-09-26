# 链表合并

## :question:题目描述
请编写一段代码，实现两个单向有序链表的合并

>输入描述:
第一行一个链表，如1 2 3 4 5
第二行一个链表，如2 3 4 5 6

>输出描述:
输出：1 2 2 3 3 4 4 5 5 6

## :bulb:解决思路
使用双指针分别指向两个链表的首节点，比较当前链表指针所指向的元素大小，较小的元素尾插入到合并的链表中，并且指针向后移动一步，而另一个指针保持不动，重复上述操作直到某个指针到了链表的尾部。**注意两个有序链表的长度不相等时，继续遍历还没有到达尾节点的链表，直接把元素插入到合并链表的尾部**，这里为了方便没有构造链表而是使用数组作为代替

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
using namespace std;
int main(void){
    int x, i, j;
    vector<int> a, b, c;
    while(cin>>x){
        a.push_back(x);
        if(cin.get() == '\n')
            break;
    }
    while(cin>>x){
        b.push_back(x);
        if(cin.get() == '\n')
            break;
    }
    for(i = 0, j = 0; i < a.size() && j < b.size();){
        if(a[i] < b[j]){
            c.push_back(a[i]);
            ++i;
        }else{
            c.push_back(b[j]);
            ++j;
        }
    }
    for(; i < a.size(); ++i)
        c.push_back(a[i]);
    for(; j < b.size(); ++j)
        c.push_back(b[j]);
    for(int k = 0; k < c.size(); ++k){
        cout<<c[k]<<' ';
    }
    return 0;
}
```
[:arrow_left:上一题:输出指定长度子串](PrintSubString.md)
[:arrow_right:下一题:括号配对问题](ParenthesesMathch.md)