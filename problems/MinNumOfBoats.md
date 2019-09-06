# 漂流船问题

## :question:题目描述
公司组织团建活动，到某漂流圣地漂流，现有如下情况：员工各自体重不一，第 i 个人的体重为 people[i]，每艘漂流船可以承载的最大重量为 limit。每艘船最多可同时载两人，但条件是这些人的重量之和最多为 limit。为节省开支，麻烦帮忙计算出载到每一个人所需的最小船只数(保证每个人都能被船载)。 

>输入描述:
第一行输入参与漂流的人员对应的体重数组，
第二行输入漂流船承载的最大重量

>输出描述:
所需最小船只数

>示例:
输入 
1 2
3
输出 1

## :bulb:解决思路
先排序，使用双指针方法，尽量让体重小的和体重大的人在一起坐船，注意最后可能只剩下中间的一个人，需要单独坐船

## :pencil2:代码
```c++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main(void){
    int x, boat, i, j, count;
    vector<int> employee;
    while(cin>>x){
        employee.push_back(x);
        if(cin.get() == '\n')
            break;
    }
    cin>>boat;
    sort(employee.begin(), employee.end());
    for(i = count = 0, j = employee.size()-1; i < j;){
        if(employee[i]+employee[j] <= boat)
            ++i;
        --j, ++count;
    }
    //跟正确答案对比发现少了以下一行通过率只有50%
    count += (i == j) ? 1 : 0;
    cout<<count<<endl;
    return 0;
}
```
[:arrow_left:上一题:解码方法](DecodeMethods.md)
[:arrow_right:下一题:推到吧骨牌](#)