# 安置路灯

## :question:题目描述
小Q正在给一条长度为n的道路设计路灯安置方案。为了让问题更简单,小Q把道路视为n个方格,需要照亮的地方用'.'表示, 不需要照亮的障碍物格子用'X'表示。小Q现在要在道路上设置一些路灯, 对于安置在pos位置的路灯, 这盏路灯可以照亮pos - 1, pos, pos + 1这三个位置。小Q希望能安置尽量少的路灯照亮所有'.'区域, 希望你能帮他计算一下最少需要多少盏路灯。     
>输入描述:
输入的第一行包含一个正整数t(1 <= t <= 1000), 表示测试用例数
接下来每两行一个测试数据, 第一行一个正整数n(1 <= n <= 1000),表示道路的长度。第二行一个字符串s表示道路的构造,只包含'.'和'X'。

>输出描述:
对于每个测试用例, 输出一个正整数表示最少需要多少盏路灯。
示例1
输入
2
3
.X.
11
...XX....XX
输出
1
3

## :bulb:解决思路
贪心算法：每遇到一个'.'，在它的下一个位置放置路灯，使得路灯尽可能照亮多的区域，然后往后跳3步，遇到'X'直接往后跳1步

## :pencil2:代码
```c++
#include <iostream>
#include <string>
using namespace std;

int main(void){
    int test_num, street_len, lantern = 0;
    string street;
    cin>>test_num;
    
    for(int i = 0; i < test_num; i++){
        cin>>street_len;
        cin>>street;
        for(int i = 0; i < street_len; ){
            if(street[i]=='.')
                lantern++,i+=3;
            else
                i++;
        }
        cout<<lantern<<endl;
        lantern = 0;
    }
    return 0;
}
```
[:arrow_left:上一题:被3整除](CountNumsDividedBy3.md)
[:arrow_right:下一题:迷路的牛牛](NiuniuIsLost.md)