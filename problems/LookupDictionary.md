# 小易的字典

## :question:题目描述
小易在学校中学习了关于字符串的理论, 于是他基于此完成了一个字典的项目。小易的这个字典很奇特, 字典内的每个单词都包含n个'a'和m个'z', 并且所有单词按照字典序排列。小易现在希望你能帮他找出第k个单词是什么。   

>输入描述:
输入包括一行三个整数n, m, k(1 <= n, m <= 100, 1 <= k <= 109), 以空格分割。

>输出描述:
输出第k个字典中的字符串，如果无解，输出-1。

>示例:
输入
2 2 6
输出
zzaa
说明
字典中的字符串依次为aazz azaz azza zaaz zaza zzaa
## :bulb:解决思路
n个'a'和m个'z'组成字符串的个数为C(m+n,m)，假设第一个字符为'a'，剩下n-1个'a'和m个'z'，个数为C(m+n-1,n-1)，如果K大于这个值，说明第一个字符是以'z'开始，转为n个'a'和m-1个'z'的子问题，否则转为n-1个'a'和m个'z'的子问题。

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int n, m, k;
    string s;
    cin>>n>>m>>k;
    while(n && m){
        long long count = 1;
        for(int i = 0; i < n-1; ++i){
            count *= n-1+m-i;
            count /= i+1;
            if(count > k)
                break;
        }
        if(k <= count){
            s.append(1, 'a');
            n--;
        }else{
            s.append(1, 'z');
            m--;
            k -= count;
        }
    }
    if(k != 1){
        cout<<-1;
        return 0;
    }
    while(n--)
        s.append(1, 'a');
    while(m--)
        s.append(1, 'z');
    cout<<s;
    return 0;
}
```
[:arrow_left:上一题:塔](AdjustTower.md)
[:arrow_right:下一题:获得最多的奖金](FindMostBonus.md)