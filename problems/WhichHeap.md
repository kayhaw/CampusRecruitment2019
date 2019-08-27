# 丰收

## :question:题目描述
又到了丰收的季节，恰逢小易去牛牛的果园里游玩。牛牛常说他对整个果园的每个地方都了如指掌，小易不太相信，所以他想考考牛牛。在果园里有N堆苹果，每堆苹果的数量为ai，小易希望知道从左往右数第x个苹果是属于哪一堆的。牛牛觉得这个问题太简单，所以希望你来替他回答。

>输入描述:
第一行一个数n(1 <= n <= 10<sup>5</sup>)。
第二行n个数a<sub>i</sub>(1 <= a<sub>i</sub> <= 1000)，表示从左往右数第i堆有多少苹果
第三行一个数m(1 <= m <= 105)，表示有m次询问。
第四行m个数q<sub>i</sub>，表示小易希望知道第q<sub>i</sub>个苹果属于哪一堆。

>输出描述:
m行，第i行输出第qi个苹果属于哪一堆。

>示例:
输入
5
2 7 3 4 9
3
1 25 11
输出
1
5
3

## :bulb:解决思路
考查二分查找，使用heap[i]存储前i堆之和，这样heap就是一个递增数组，使用二分法，类似二分查找，但此时我们要找的是一个区间而不是数，所以如果while条件是left < right的话可能会变成死循环，我们让right-left=1时退出循环，此时确定区间为[a,b]，确定结果就很简单了，当num<=a时，在第left+1堆，否则在第right+1堆

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int which_heap(int* heaps, int num, int length);
int main(void){
    int n, m, pre = 0, query;
    cin>>n;
    int *num = new int[n]();
    for(int i = 0; i < n; ++i){
        cin>>num[i];
        num[i] += pre;
        pre = num[i];
    }
    cin>>m;
    for(int i = 0; i < m; ++i){
        cin>>query;
        cout<<which_heap(num, query, n)<<endl;
    }
    delete num;
    return 0;
}
int which_heap(int* heap, int num, int length){
    int left = 0, right = length-1, mid;
    while(left+1 < right){
        mid = (left+right)/2;
        if(heap[mid] == num)
            return mid+1;
        else if(heap[mid] < num)
            left = mid;
        else
            right = mid;
    }
    return (num <= heap[left]) ? left+1 : right+1;
}
```
[:arrow_left:上一题:瞌睡](TakeANap.md)
[:arrow_right:下一题:整理房间](CleanUpRoom.md)