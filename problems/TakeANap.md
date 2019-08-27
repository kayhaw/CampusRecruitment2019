# 瞌睡

## :question:题目描述
小易觉得高数课太无聊了，决定睡觉。不过他对课上的一些内容挺感兴趣，所以希望你在老师讲到有趣的部分的时候叫醒他一下。你知道了小易对一堂课每分钟知识点的感兴趣程度，并以分数量化，以及他在这堂课上每分钟是否会睡着，你可以叫醒他一次，这会使得他在接下来的k分钟内保持清醒。你需要选择一种方案最大化小易这堂课听到的知识点分值。   

>输入描述:
第一行 n, k (1 <= n, k <= 105) ，表示这堂课持续多少分钟，以及叫醒小易一次使他能够保持清醒的时间。
第二行 n 个数，a<sub>1</sub>, a<sub>2</sub>, ... , a<sub>n</sub>(1 <= a<sub>i</sub> <= 104) 表示小易对每分钟知识点的感兴趣评分。
第三行 n 个数，t<sub>1</sub>, t<sub>2</sub>, ... , t<sub>n</sub> 表示每分钟小易是否清醒, 1表示清醒。

>输出描述:
小易这堂课听到的知识点的最大兴趣值。

>示例:
输入
6 3
1 3 5 2 5 4
1 1 0 1 0 0
输出
16

## :bulb:解决思路
遍历数组，求出在每个0位置叫醒的兴趣值，取最大值
- 要区分那些本来就是醒着的，哪些是睡着的，计算分数时不能有重复
- 使用k大小的滑动窗口，每次向前滑动1步，出窗口的0要减去相应的分数，进窗口的0要加上相应的分数

## :pencil2:代码
```c++
#include <iostream>
#include <algorithm>
using namespace std;
int main(void){
    int n, k;
    cin>>n>>k;
    int* score = new int[n]();
    int* sober = new int[n]();
    int base = 0, cur = 0, maximum = 0;
    
    for(int i = 0; i < n; ++i){
        cin>>score[i];
    }
    for(int i = 0; i < n; ++i){
        cin>>sober[i];
    }
    for(int i = 0; i < n; ++i){
        base += score[i]*sober[i];
    }
    k = min(k, n);
    for(int i = 0; i < k; ++i)
        cur += (!sober[i]) ? score[i] : 0;
    maximum = cur;
    for(int i = k; i < n; ++i){
        if(!sober[i])
            cur+=score[i];
        if(!sober[i-k])
            cur-=score[i-k];
        maximum = max(cur, maximum);
    }
    cout<<base+maximum;
    delete[] score;
    delete[] sober;
    return 0;
}
```
[:arrow_left:上一题:俄罗斯方块](PlayTetris.md)
[:arrow_right:下一题:丰收](WhichHeap.md)