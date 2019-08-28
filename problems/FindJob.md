# 牛牛找工作

## :question:题目描述
为了找到自己满意的工作，牛牛收集了每种工作的难度和报酬。牛牛选工作的标准是在难度不超过自身能力值的情况下，牛牛选择报酬最高的工作。在牛牛选定了自己的工作后，牛牛的小伙伴们来找牛牛帮忙选工作，牛牛依然使用自己的标准来帮助小伙伴们。牛牛的小伙伴太多了，于是他只好把这个任务交给了你。

>输入描述:
每个输入包含一个测试用例。
每个测试用例的第一行包含两个正整数，分别表示工作的数量N(N<=100000)和小伙伴的数量M(M<=100000)。
接下来的N行每行包含两个正整数，分别表示该项工作的难度Di(Di<=1000000000)和报酬Pi(Pi<=1000000000)。
接下来的一行包含M个正整数，分别表示M个小伙伴的能力值Ai(Ai<=1000000000)。
保证不存在两项工作的报酬相同。

>输出描述:
对于每个小伙伴，在单独的一行输出一个正整数表示他能得到的最高报酬。一个工作可以被多个人选择。

>示例
输入
3 3 
1 100 
10 1000 
1000000000 1001 
9 10 1000000000
输出
100 
1000 
1001

## :bulb:解决思路
按照工作难度和报酬进行排序，然后二分法查找，这里要注意有些难度大的工作反而报酬小，在进行排序后还需要在遍历一遍数组将报酬更新为之前难度小工作中报酬最大的，使用二分查找时注意循环退出条件以及返回值

## :pencil2:代码
```c++
#include <bits/stdc++.h>
using namespace std;
int BinSearch(vector<pair<int, int>> &jobs, const int &ai, const int &N){
    int left = 0, right = N-1, mid;
    while(left <= right){
        mid = left + (right-left)/2;
        //难度超过了能力范围肯定不行，要减去1
        if(jobs[mid].first > ai)
            right = mid-1;
        else
            left = mid+1;
    }
    //能力过小
    if(!left)
        return 0;
    //能力过大
    else if(jobs[right].first <= ai)
        return jobs[right].second;
    else
        return jobs[left-1].second;
}
int main(void){
    int N, M, Di, Pi, Ai, max = 0;
    vector<pair<int,int>> jobs;
    vector<int> friends;
    cin>>N>>M;
    for(int i = 0; i < N; ++i){
        cin>>Di>>Pi;
        jobs.push_back({Di, Pi});
    }
    for(int i = 0; i < M; ++i){
        cin>>Ai;
        friends.push_back(Ai);
    }
    sort(jobs.begin(), jobs.end());
    //用for each循环的话得到的是读写副本，不会真的改变报酬
    for(int i = 0; i < N; ++i){
        if(jobs[i].second > max)
            max = jobs[i].second;
        else
            jobs[i].second = max;
    }
    for(int ai : friends)
        cout<<BinSearch(jobs, ai, N)<<endl;
    return 0;
}
```
[:arrow_left:上一题:无](#)
[:arrow_right:下一题:被3整除](CountNumsDividedBy3.md)