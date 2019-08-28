# 获得最多的奖金

## :question:题目描述
小明在越南旅游，参加了当地的娱乐活动。小明运气很好，拿到了大奖，到了最后的拿奖金环节。小明发现桌子上放着一列红包，每个红包上写着奖金数额。现在主持人给要求小明在这一列红包之间“切”2刀，将这一列红包“切”成3组，并且第一组的奖金之和等于最后一组奖金和（允许任意一组的红包集合是空）。最终第一组红包的奖金之和就是小明能拿到的总奖金。小明想知道最多能拿到的奖金是多少，你能帮他算算吗。举例解释：桌子上放了红包  1, 2, 3, 4, 7, 10。小明在“4,7”之间、“7,10” 之间各切一刀，将红包分成3组 [1, 2, 3, 4]   [7]   [10]，其中第一组奖金之和=第三组奖金之和=10，所以小明可以拿到10越南盾。    

>输入描述:
第一行包含一个正整数n，(1<=n<= 200 000)，表示有多少个红包。
第二行包含n个正整数d[i]，表示每个红包包含的奖金数额。其中1<= d[i] <= 1000 000 000

>输出描述:
小明可以拿到的总奖金

>示例:
输入
5
1 3 1 1 4
输出
5
## :bulb:解决思路
左右指针遍历，左边第一堆的总和小左指针右移，右边第三堆的总和小右指针左移，**注意找到第一堆等于第三堆不要停止遍历，后面可能还会相等，而且相等的话值肯定会比上一次的大，所以不用比较直接更新结果**，循环停止的条件是左右指针相遇，结果maximum初始化为0，这样没有符合条件的情况时输出0。

## :pencil2:代码
```c++
#include <iostream>
using namespace std;
int main(void){
    int n;
    cin>>n;
    long long first_heap, third_heap;
    long long maximum = 0;
    int* num = new int[n]();
    for(int i = 0; i < n; ++i){
        cin>>num[i];
    }
    first_heap = num[0], third_heap = num[n-1];
    for(int left = 0, right = n-1; left < right; ){
        if(first_heap < third_heap){
            ++left;
            first_heap += num[left];
        }
        else if(first_heap > third_heap){
            --right;
            third_heap += num[right];
        }
        else{
            maximum = first_heap;
            ++left;
            --right;
            first_heap += num[left];
            third_heap += num[right];
        }
    }
    cout<<maximum;
    return 0;
}
```
[:arrow_left:上一题:小易的字典](LookupDictionary.md)
[:arrow_right:下一题:将满二叉树转换为求和树](ConvertFBT.md)